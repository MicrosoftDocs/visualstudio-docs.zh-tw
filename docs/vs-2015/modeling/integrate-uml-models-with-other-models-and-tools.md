---
title: 整合 UML 模型與其他模型和工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b85ad2e150880042125782349120d271ff2b7d7a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290286"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>整合 UML 模型與其他模型及工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 模型可以與其他模型及網域指定的語言整合。  
  
 您可以藉由撰寫擴充功能程式碼以執行不同函式，來使用下列方式整合模型：  
  
 將來自任何項目的參考附加至其他項目 (例如檔案) 或其他模型內的項目。  
 在 UML 項目中，您可以藉由將其他 UML 項目、檔案或其他物件編碼為字串，以儲存連結至此。  
  
 例如，您可以將能夠連結任何 UML 動作 (也就是活動圖表中的項目) 的擴充功能寫入至另一個活動圖表。 當使用者按兩下動作時，其他圖表隨即開啟。 這可讓使用者提供動作的更詳細檢視。  
  
 您可以用兩種方式，將字串和任何項目中的其他資料儲存在內：  
  
-   **造型屬性。** 您可以定義 UML 設定檔，在設定檔中，能夠定義會將屬性加入 UML 項目指定類型的造型。 例如，您可以在其中定義新增名為屬性的設定檔**moredetail 動作**加入 UML 動作。 您可以藉由將造型套用至動作，然後將資料儲存在屬性中，來撰寫可以在動作中儲存連結資料的擴充功能程式碼。  
  
     使用者可以在 [屬性] 視窗中看見此造型及其屬性。  
  
     若要部署此擴充功能，您將把設定檔定義和擴充功能程式碼封裝在單一 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 擴充功能中。  
  
     如需詳細資訊，請參閱 <<c0> [ 定義要擴充 UML 的設定檔](../modeling/define-a-profile-to-extend-uml.md)。  
  
     如需範例專案，在其中一個設定檔部署以及功能表命令和軌跡處理常式，請參閱[範例： UML 設定檔](http://go.microsoft.com/fwlink/?LinkID=213811)。  
  
-   **參考。** 您可以將一組字串附加至任何 UML 項目。 您可以撰寫儲存資訊 (例如檔案名稱或其他項目之 GUID) 的程式碼。 不需提供其他定義便可以完成。 使用者無法直接查看參考。  
  
     如需詳細資訊，請參閱 <<c0> [ 將參考字串附加至 UML 模型項目](../modeling/attach-reference-strings-to-uml-model-elements.md)。 如需範例，請參閱[UML 項目連結至圖表或其他檔案](http://go.microsoft.com/fwlink/?LinkId=213813)。  
  
 將參考編碼至模型項目有兩種方式：  
  
-   **GUID 及檔名**目標模型項目和模型，其中包含它，或特定的圖表，以顯示它。  
  
     如需範例，請參閱[UML 項目連結至圖表或其他檔案](http://go.microsoft.com/fwlink/?LinkId=213813)。  
  
-   **ModelBus 參考。** ModelBus 是用來建立及解析模型之間參考的架構。 它包含 ModelBus 選擇器，可讓使用者在模型中選取項目。 它也會協助使用者解析因目標模型內的變更而遺失的參考。  
  
     如需詳細資訊，請參閱 <<c0> [ 使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)。  
  
 將變更從一個模型散佈至另一個。  
 例如，您可以同步處理項目名稱和已連結圖表的名稱，這樣一來，如果使用者變更其中一個，另一個也會變更。 有兩種機制來執行這項操作：  
  
1.  **VMSDK 規則**可以用來散佈相同模型內的變更。  
  
     如需範例，請參閱[UML 項目連結至圖表或其他檔案](http://go.microsoft.com/fwlink/?LinkId=213813)。  
  
2.  **VMSDK 事件**可用傳播模型外的變更，例如，若要變更連結的文件中，檔案名稱或變更另一個模型中的項目。  
  
 如需這兩種機制的資訊，請參閱[如何： 回應 UML 模型中的變更](../misc/how-to-respond-to-changes-in-a-uml-model.md)。  
  
 拖曳項目，以將其從一個模型複製到另一個模型  
 您可將項目拖曳到 UML 圖表上，讓使用者建立項目。 建立的項目可以不是原始項目的副本。 例如，您可讓使用者將活動圖表從方案總管拖曳至另一個活動圖表上，以建立新的動作。  
  
 如需詳細資訊，請參閱[在模型圖上定義軌跡處理常式](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)並[如何： 加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)。  
  
## <a name="samples"></a>範例  
 程式碼範例，請參閱[UML 項目連結至圖表或其他檔案](http://go.microsoft.com/fwlink/?LinkId=213813)。 此範例讓使用者將檔案拖曳到任何 UML 項目，並稍後按兩下檔案項目以開啟檔案。 例如，您可以將活動圖表連結至使用案例項目。 圖示會顯示哪些項目具有連結。  
  
 這個程式碼範例會示範下列技術：  
  
-   [將參考字串附加至 UML 模型項目](../modeling/attach-reference-strings-to-uml-model-elements.md)  
  
     範例程式碼會將檔案路徑和項目 GUID 儲存與項目相關聯的參考字串中。  
  
-   如何將裝飾項目加入 UML 項目。 如需裝飾項目的一般資訊，請參閱 <<c0> [ 自訂文字和影像欄位](../modeling/customizing-text-and-image-fields.md)。  
  
     此範例會將影像裝飾項目加入 UML 圖形。  
  
-   [如何：回應 UML 模型中的變更](../misc/how-to-respond-to-changes-in-a-uml-model.md)  
  
     此範例將示範如何定義會回應出現在圖表上之新圖形的規則。  
  
-   [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
-   [在模型圖表上定義軌跡處理常式](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)  
  
     此範例將示範如何處理拖曳自 Windows 檔案總管 (或檔案總管)、方案總管及其他 UML 項目的項目。  
  
 針對由 DSL 讀取 UML 模型的範例，請參閱[如何： 加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [在模型圖上定義軌跡處理常式](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [如何： 加入拖放處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [如何： 回應 UML 模型中的變更](../misc/how-to-respond-to-changes-in-a-uml-model.md)   
 [範例： UML 設定檔](http://go.microsoft.com/fwlink/?LinkID=213811)   
 [UML 項目連結至圖表或其他檔案](http://go.microsoft.com/fwlink/?LinkId=213813)



