---
title: "在單一解決方案中的多個 Dsl |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: e7b1ef7fc26cb0e46ecaf1853d6c9490016e68a5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="multiple-dsls-in-one-solution"></a>一個方案中有多個 DSL
您可以將數個 DSL 封裝成單一方案的一部分，以便能夠一起安裝。  
  
 用來整合多個 DSL 的方法有幾種。 如需詳細資訊，請參閱[整合的模型，使用 Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)和[如何： 加入拖放的處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)和[自訂複製行為](../modeling/customizing-copy-behavior.md)。  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>在同一個方案中建置多個 DSL  
  
1.  建立兩個或多個 DSL 方案和一個 VSIX 專案，然後將所有專案加入至一個方案。  
  
    -   若要建立新的 VSIX 專案： 在**新專案**對話方塊中，選取**Visual C#**，**擴充性**， **VSIX 專案**。  
  
    -   在 VSIX 方案目錄中建立兩個或多個 DSL 方案。  
  
         針對每個 DSL，開啟 Visual Studio 的新執行個體。 建立新的 DSL，然後指定與 VSIX 方案相同的方案資料夾。  
  
         確定使用不同的副檔名建立各個 DSL。  
  
    -   變更名稱**Dsl**和**DslPackage**專案，使其完全不同。 例如：`Dsl1`、`DslPackage1`、`Dsl2`、`DslPackage2`。  
  
    -   在每個**DslPackage\*\source.extension.tt**，這行更新為正確的 Dsl 專案名稱：  
  
         `string dslProjectName = "Dsl2";`  
  
    -   在 VSIX 方案中，加入 Dsl * 和 DslPackage\*專案。  
  
         您可能想將每組專案置於各自的方案資料夾中。  
  
2.  合併 DSL 的 VSIX 資訊清單：  
  
    1.  開啟 * YourVsixProject ***\source.extension.manifest**。  
  
    2.  針對每個 DSL 選擇**將內容加入**並加入：  
  
        -   `Dsl*`專案做為**MEF 元件**  
  
        -   `DslPackage*`專案做為**MEF 元件**  
  
        -   `DslPackage*`專案做為**VS 套件**  
  
3.  建置方案。  
  
 產生的 VSIX 會同時安裝這兩個 DSL。 您可以測試它們，使用 F5，或部署 * YourVsixProject ***\bin\Debug\\\*.vsix**。  
  
## <a name="see-also"></a>請參閱  
 [使用 Visual Studio Modelbus 整合模型](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [如何： 加入拖放的處理常式](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [自訂複製行為](../modeling/customizing-copy-behavior.md)