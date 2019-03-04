---
title: Associação de entidades de OData de gerenciamento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860822"
---
# <a name="associating-management-odata-entities"></a>Associar entidades OData de gerenciamento

Geralmente é útil criar uma associação entre duas entidades de OData de gerenciamento diferentes. Por exemplo, um serviço OData de gerenciamento pode ter entidades que gerenciam um catálogo de produtos que são organizados em categorias e definir as entidades `Product` e `Category`. Ao associar essas duas entidades, um cliente pode obter informações sobre todos os produtos em uma categoria com uma única solicitação ao serviço web.

Um exemplo que mostra como criar associações entre entidades pode ser baixado em [exemplo de associação](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Criar a associação no arquivo de esquema do recurso

O MOF a seguir define duas entidades. Vamos criar uma associação entre eles.

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

O `Category` classe define uma propriedade que é uma matriz de nomes de produtos que pertencem a essa categoria.

Para associar duas entidades, você deve definir uma classe com o `Association` atributo no arquivo MOF de esquema de recurso para o serviço. A classe deve definir as duas entidades a serem associadas, chamado `ends` da associação. O exemplo a seguir mostra uma definição de uma classe que define uma associação entre as entidades de categoria e produtos.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Você também deve alterar a declaração da propriedade produtos na classe de categoria. Você usa o `AssociationClass` palavra-chave para especificar que a propriedade é uma extremidade da associação. A propriedade também deve ser definida como uma referência a uma entidade separada, em vez de uma matriz de cadeias de caracteres. Você pode fazer isso usando o `ref` palavra-chave. O exemplo a seguir mostra a definição de propriedade para a associação.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Por fim, você deve declarar a outra extremidade da associação com a adição de uma definição de propriedade para o `Product` classe. Esta é uma referência para uma matriz ou uma única entidade. Supondo que cada produto pertence a apenas uma categoria, a definição seria da seguinte maneira.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

As propriedades que representam as duas extremidades de associação são chamadas de propriedades de navegação.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Etapas para a associação de entidades no arquivo de esquema do recurso

- Definir a associação como uma classe usando o `Association` palavra-chave.

- Defina as extremidades de associação usando a palavra-chave AssociationClass para qualificar as propriedades das entidades associadas.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Criar a associação no arquivo XML de mapeamento de recursos

Há três casos diferentes a serem considerados ao mapeamento de uma associação no arquivo XML de mapeamento do recurso.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Determinando como associar entidades no arquivo de mapeamento de recursos

- Se a propriedade de navegação está presente no subjacente. Tipo do .NET framework, e a propriedade contém chaves estrangeiras, nenhum mapeamento explícito é necessário.

- Se a propriedade de navegação não existe no tipo subjacente do .NET Framework, você deve especificar um cmdlet que recupera a lista de chaves das instâncias associadas. Faça isso adicionando um `Association` elemento aninhado sob o `CmdletImplementation` elemento, seguindo os elementos que definem o `cmdlets` para outros comandos CRUD.

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- Se a propriedade de navegação existe no tipo subjacente do .NET Framework, mas ele contém instâncias de objeto, em vez de chaves estrangeiras, você deve criar um cmdlet (escrevendo um script ou função do Windows PowerShell) para recuperar as chaves estrangeiras. Você especificar, em seguida, esse cmdlet no arquivo de mapeamento do recurso. Por exemplo, o script para recuperar as chaves seria semelhante ao seguinte.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  E o XML no arquivo de mapeamento do recurso seria semelhante ao seguinte.

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- Além de especificar um cmdlet para recuperar as entidades associadas, você também pode especificar os cmdlets para adicionar e remover referências da coleção. O exemplo a seguir pressupõe que os cmdlets ProductToCategory adicionar e remover ProductFromCategory existe (eles também podem ser definidos em um script ou função do exemplo anterior).

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a>Consultando entidades associadas

O cliente poderá recuperar uma lista de instâncias associado a uma entidade com a criação de consultas específicas.

#### <a name="constructing-queries-for-associated-entities"></a>Construir consultas para entidades associadas

- Um cliente pode solicitar os detalhes de uma categoria sem recuperar seus produtos associados. Por exemplo, a solicitação a seguir obtém detalhes do `food` categoria.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Para obter os produtos associados da categoria (mas não os detalhes da categoria em si, o cliente especifica a propriedade de navegação na solicitação.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Para recuperar apenas as URLs dos produtos, use o `$links` qualificador na solicitação.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- O cliente pode obter os detalhes de categoria e seus produtos associados usando o `$expand` qualificador.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Consulte Também

[Criar um serviço Web de extensão de IIS OData de gerenciamento](./creating-a-management-odata-web-service.md)