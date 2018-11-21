---
title: 定義套件和命名空間 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b9295b5af83270069df11e6460ee85dfe0fd9c73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741900"
---
# <a name="define-packages-and-namespaces"></a>定義套件和命名空間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，*封裝*是 UML 項目，例如類別、 使用案例和元件定義的容器。 套件也可以包含其他套件。  
  
 在 [UML 模型總管] 中，套件內的所有定義都是套件下的巢狀套件。 UML 模型是一種套件，並形成樹狀結構的根目錄。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="in-this-topic"></a>本主題內容  
 [命名空間](#Namespaces)  
  
 [建立和檢視套件](#Packages)  
  
 [建立套件內的模型項目](#Elements)  
  
 [將項目移入或移出套件](#Moving)  
  
 [將項目貼入套件](#Pasting)  
  
 [匯入套件之間的關聯性](#Import)  
  
 [參考至另一個命名空間](#References)  
  
 [封裝的屬性](#Properties)  
  
##  <a name="Namespaces"></a> 命名空間  
 套件適用於將工作分成不同區域。 每個套件都定義命名空間，讓不同套件中所定義的名稱彼此不衝突。  
  
 每個項目的限定名稱屬性是所屬套件的限定名稱，後面加上項目本身名稱。 例如，如果您的套件稱為 `MyPackage`，則套件內的類別會有限定名稱 (例如 `MyPackage::MyClass`)。 因為每個項目都是包含在模型內，所以每個限定名稱的開頭是模型名稱。  
  
 模型也會定義命名空間，讓模型中每個項目的限定名稱開頭是模型名稱。  
  
 其他模型項目也會定義命名空間。 例如，作業屬於其父類別所定義的命名空間，讓其限定名稱類似 `MyModel ::MyPackage ::MyClass ::MyOperation`。 同樣地，動作屬於其父活動所定義的命名空間。  
  
 套件是容器。 如果您移動或刪除套件，則也會移動或刪除類別、套件以及其內所定義的其他項目。 定義命名空間的其他項目也是如此。  
  
##  <a name="Packages"></a> 建立和檢視套件  
 您可以在 UML 類別圖或 [UML 模型總管] 中建立套件。  
  
#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>在 UML 類別圖中建立套件  
  
1.  開啟 UML 類別圖，或建立新的 UML 類別圖。  
  
2.  按一下 **封裝**工具。  
  
3.  按一下圖表上的任何位置。 新的套件圖形隨即出現。  
  
     您可以按一下現有套件，讓某個套件成為另一個套件中的巢狀套件。  
  
4.  輸入套件的新名稱。  
  
#### <a name="to-create-a-package-in-uml-model-explorer"></a>在 UML 模型總管中建立套件  
  
1. 開啟**UML 模型總管**。 在 [**架構**功能表上，指向**Windows**，然後按一下**UML 模型總管]**。  
  
2. 以滑鼠右鍵按一下您要加入新套件的套件或模型。  
  
   > [!NOTE]
   >  您可以讓某個套件成為另一個套件內的巢狀套件。  
  
3. 指向**新增**，然後按一下**封裝**。  
  
    新的套件隨即出現在模型中。  
  
4. 輸入套件的新名稱。  
  
   如果您已在 [UML 模型總管] 中建立套件，則可以將它顯示在 UML 類別圖中。 您也可以在多個 UML 類別圖上顯示套件。  
  
#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>在 UML 類別圖上顯示現有套件  
  
-   將套件從 [UML 模型總管] 拖曳至類別圖。  
  
    > [!NOTE]
    >  這會在此圖表上建立套件的檢視。 不一定會顯示套件所含的所有項目。 若要確定您看到所有套件內容，請在 [UML 模型總管] 中進行檢視。  
  
##  <a name="Elements"></a> 建立套件內的模型項目  
 有四種方式可將模型項目放到套件內：  
  
- 將新的項目加入 [UML 模型總管] 中的套件。  
  
- 將類別和其他類型加入 UML 類別圖中的套件。  
  
- 設定**LinkedPackage**圖表的屬性，讓圖表上建立新的項目會放在您指定之套件內。 使用這種方式，可以將類別圖、元件圖和使用案例圖連結至套件。  
  
- 將項目移入或移出 [UML 模型總管] 中的套件。  
  
  套件中的項目會出現在 [UML 模型總管] 中的套件，而其限定名稱的開頭是套件的限定名稱。 若要查看任何項目的限定的名稱，以滑鼠右鍵按一下項目，然後按一下**屬性**。 **限定名稱**屬性會出現在**屬性**視窗。  
  
#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>在 UML 模型總管的套件中建立項目  
  
1.  開啟**UML 模型總管**。 在上**檢視**功能表上，指向**其他 Windows**，然後按一下**UML 模型總管**。  
  
2.  以滑鼠右鍵按一下您要加入新項目的套件或模型。  
  
3.  指向**新增**，然後按一下您想要新增的項目類型。  
  
     新的項目會出現在套件下方。  
  
4.  輸入新項目的名稱。  
  
    > [!NOTE]
    >  新的項目不會出現在任何圖表上。 若要建立新項目的檢視，您可以將它從 [UML 模型總管] 拖曳至圖表。 圖表必須是顯示這種項目的類型。  
  
#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>在 UML 類別圖的套件中建立項目  
  
1.  開啟套件所在的類別圖。  
  
    -   建立新的套件 (如果您還沒有這麼做)。  
  
    -   若要讓現有套件出現在類別圖上，您可以將從套件拖曳**UML 模型總管**拖曳至類別圖表。  
  
2.  按一下類別、介面、列舉或套件的工具。  
  
3.  按一下您要放置新項目的套件。  
  
     新的項目會出現在套件內。  
  
#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>建立所指定套件中圖表的所有項目  
  
1.  建立套件 (如果您還沒有這麼做)。  
  
2.  開啟元件圖、使用案例圖或 UML 類別圖。  
  
3.  開啟圖表的屬性。 以滑鼠右鍵按一下圖表的空白部分，然後按一下**屬性**。  
  
4.  在 **連結的套件**屬性中，選擇您想要包含圖表內容的套件。  
  
5.  在圖表中建立新項目。 這些將會放置到套件中。  
  
    -   **限定名稱**每個元素的開頭是套件的限定名稱。  
  
    -   在 [ **UML 模型總管]**，每個項目會出現在套件下方。  
  
##  <a name="Moving"></a> 將項目移入和移出套件  
 您可以將一或多個項目移入或移出套件。  
  
 如果您移動套件，也會移動其內的所有項目。  
  
#### <a name="to-move-an-element-into-or-out-of-a-package"></a>將項目移入或移出套件  
  
-   在 [UML 模型總管] 中，將項目拖曳至或拖曳出根目錄是套件的樹狀結構。  
  
     項目的限定名稱會變更，以顯示其新擁有套件或模型。  
  
     \-或-  
  
-   在類別圖中，將項目拖曳至套件圖形。  
  
     項目的限定名稱會變更，以顯示其新擁有套件。  
  
    > [!NOTE]
    >  如果您將項目從套件拖曳至圖表的空白部分，則其擁有套件不會變更。 這可讓您製作圖表來顯示數個套件中的項目，而不需顯示套件本身。  
  
##  <a name="Pasting"></a> 將項目貼入套件  
 您可以將項目貼入套件中。 如果您將一組相關項目貼入套件，則也會貼上其間的關聯性。  
  
#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>將項目貼入 UML 類別圖上的套件  
  
1.  在 UML 類別圖上，選取您要複製的所有項目。 以滑鼠右鍵按一下其中一個，然後按一下 **複製**。  
  
2.  以滑鼠右鍵按一下封裝，然後按一下**貼上**。  
  
    > [!NOTE]
    >  套件可以在不同的圖表上。  
  
##  <a name="Import"></a> 匯入套件之間的關聯性  
 您可以定義匯入套件之間關聯性，使用**匯入**工具。  
  
 匯入表示所匯入套件中定義的項目 (即關聯性箭號端的項目) 也有效地定義於匯入中套件。 其可見性會定義為任何項目**封裝**中匯入中套件也會顯示。  
  
 請避免在匯入關聯性中建立迴圈。  
  
##  <a name="References"></a> 參考至另一個命名空間  
 如果您想要從另一個套件參照某個套件的項目，則必須使用項目的限定名稱。  
  
 例如，假設套件 `SalesCommon` 定義類型 `CustomerAddress`。 在另一個套件 `RestaurantSales` 中，您想要定義類型 `MealOrder`，其中包含 Customer Address 類型的屬性。 您有兩種選擇：  
  
-   使用完整名稱 `SalesCommon::CustomerAddress`，指定屬性的類型。 您應該做才`CustomerAddress`有其**可視性**屬性設定為**公用**。  
  
-   建立從 `RestaurantSales` 套件到 `SalesCommon` 套件的匯入關聯性。 接著，您可以使用 `CustomerAddress`，而不使用它的限定名稱。  
  
##  <a name="Properties"></a> 封裝的屬性  
 每個套件都具有下列屬性。 若要查看屬性，以滑鼠右鍵按一下封裝，在圖表上或在 [UML 模型總管] 中，然後**屬性**。  
  
|屬性|預設值|描述|  
|--------------|-------------------|-----------------|  
|**名稱**|(新名稱)|套件名稱。 您可以在圖表或 [屬性] 視窗中對其進行變更。|  
|**限定的名稱**|*容器*::*封裝名稱*|完整名稱，但前面加上包含此套件之套件或模型的名稱。 如需詳細資訊，請參閱[命名空間](#Namespaces)。|  
|**設定檔**|(空白)|連結至此套件的設定檔清單。 這些設定檔提供可套用至套件內項目的造型。 如需詳細資訊，請參閱 <<c0> [ 來自訂您的模型，使用設定檔和造型](../modeling/customize-your-model-with-profiles-and-stereotypes.md)。|  
|**可見度**|**Public**|套件在其父套件外部的可見性。|  
|**工作項目**|(空白)|連結的工作項目清單。 如需詳細資訊，請參閱 <<c0> [ 連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)。|  
|**定義位置**|(名稱)|儲存套件詳細資料的檔案名稱。 這些檔案是在**ModelDefinition**專案資料夾。 這項資訊可用於進行原始檔控制。|  
|**描述**|(空白)|套件的描述。|  
|**造型**|(空白)|套用至此套件的造型。 可用的造型清單取決於您為此套件所選擇的設定檔，以及包含它的套件。 如需詳細資訊，請參閱 <<c0> [ 來自訂您的模型，使用設定檔和造型](../modeling/customize-your-model-with-profiles-and-stereotypes.md)。|  
  
## <a name="how-packages-are-stored"></a>套件的儲存方式  
 當您建立新封裝時，新 **.uml**中建立檔案時**ModelDefinition**專案資料夾。 根模型，這也是封裝，也會儲存在 **.uml**檔案。  
  
 此外，每個圖表儲存在兩個檔案，其中一個代表圖表的圖形，以及 **.layout**檔案則記錄圖形的位置。  
  
## <a name="see-also"></a>另請參閱  
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)   
 [UML 類別圖： 參考](../modeling/uml-class-diagrams-reference.md)   
 [UML 類別圖： 方針](../modeling/uml-class-diagrams-guidelines.md)   
 [在版本控制下管理模型與圖表](../modeling/manage-models-and-diagrams-under-version-control.md)



