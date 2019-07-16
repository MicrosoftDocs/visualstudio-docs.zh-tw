---
title: 在 UML 模型中建立項目和關聯性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ce1f236347ad811f1c5d115f30907b7e3356e3af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159639"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>在 UML 模型中建立項目和關聯性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 擴充功能的程式碼中，您可以建立及刪除項目和關聯性。  
  
## <a name="create-a-model-element"></a>建立模型項目  
  
### <a name="namespace-imports"></a>命名空間匯入  
 必須包含下列 `using` 陳述式：  
  
 建立方法會定義為此命名空間中的擴充方法：  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>取得您要建立之項目的擁有者  
 模型會形成單一樹狀結構，如此除了模型根項目之外，每一個項目都會有一個擁有者。 模型根項目的類型為 `IModel`，它是屬於 `IPackage` 的類型。  
  
 如果您建立將在特殊圖表中顯示的項目，例如使用者目前的圖表，通常應該要在連結至該圖表的套件中建立該項目。 例如：  
  
```  
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;  
```  
  
 本表摘要說明一般模型項目的擁有權：  
  
|要建立的項目|Owner|  
|---------------------------|-----------|  
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|  
|`IAttribute, IOperation`|`IClass, IInterface`|  
|`IPart, IPort`|`IComponent`|  
|`IAction, IObjectNode`|`IActivity`|  
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|  
  
### <a name="invoke-the-create-method-on-the-owner"></a>在擁有者上叫用 Create 方法  
 方法名稱是格式的：`Create`*擁有的類型*`()`。 例如：  
  
```  
IUseCase usecase1 = linkedPackage.CreateUseCase();  
```  
  
 某些類型的建立方法較為複雜，尤其是在循序圖中。 請參閱[使用 UML API 編輯 UML 循序圖](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)。  
  
 針對某些類型的項目，您可以在其存留期內使用 `SetOwner(newOwner)` 變更項目的擁有者。  
  
### <a name="set-the-name-and-other-properties"></a>設定名稱和其他屬性  
  
```  
usecase1.Name = "user logs in";  
```  
  
### <a name="example"></a>範例  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Extensions;  
...  
 void InstantiateObserverPattern (IPackage package, string namePrefix)  
 {    IInterface observer = package.CreateInterface();  
      observer.Name = namePrefix + "Observer";  
      IOperation operation = observer.CreateOperation();  
      operation.Name = "Update";  
      IClass subject = package.CreateClass();  
      subject.Name = namePrefix + "Subject"; ...  
```  
  
## <a name="create-an-association"></a>建立關聯  
  
#### <a name="to-create-an-association"></a>建立關聯  
  
1. 取得關聯的擁有者，這通常是包含關聯性來源端的套件或模型。  
  
2. 在擁有者上叫用必要的 Create 方法。  
  
3. 設定關聯性的屬性，例如其名稱。  
  
     例如：  
  
    ```  
    IAssociation association = subject.Package.CreateAssociation(subject, observer);  
    association .Name = "Observes";  
    ```  
  
4. 設定關聯性各端的屬性。 總是會有兩個 `MemberEnds`。 例如：  
  
    ```  
    association .MemberEnds[0].Name = "subject";   // role name  
    association .MemberEnds[1].Name = "observers"; // role name  
    association .MemberEnds[1].SetBounds("0..*");           
                // multiplicity defaults to "1"  
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;  
    ```  
  
## <a name="create-a-generalization"></a>建立一般化  
  
```  
IGeneralization generalization =   
  subclass.CreateGeneralization(superClass);  
```  
  
## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>從模型刪除項目、關聯性或一般化  
  
```  
anElement.Delete();  
```  
  
 當您從模型刪除項目時：  
  
- 也會刪除與項目連結的每一個關聯性。  
  
- 也會刪除在圖表上代表該項目的每一個圖形。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)   
 [在圖表上顯示 UML 模型](../modeling/display-a-uml-model-on-diagrams.md)
