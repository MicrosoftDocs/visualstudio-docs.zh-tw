---
title: "字型和色彩概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13a2a8b584af507f8937fd6abb46c85f329de0b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="font-and-color-overview"></a>字型和色彩概觀
本主題討論中的文字字型和色彩設定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 它也介紹的概念分類和顯示項目，並說明 Vspackage 和核心編輯器如何使用文字屬性。  
  
## <a name="the-fonts-and-colors-property-page"></a>字型和色彩 屬性頁面  
 您可以管理屬性中顯示的文字[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]透過整合式的開發環境 (IDE)**字型和色彩**屬性頁。 若要尋找**字型和色彩**屬性頁面上**工具**功能表上，按一下 **選項**。 展開**環境**，然後按一下 **字型和色彩**。  
  
## <a name="categories-and-display-items"></a>分類和顯示項目  
 字型和色彩會組織成**類別**和**顯示項目**。  
  
-   A**類別**是邏輯或功能的容器數目的**顯示項目**。  
  
     一份**類別**處於**顯示設定**的下拉式清單方塊**字型和色彩**屬性頁。  
  
-   A**顯示項目**是妥善定義的文字實體，例如註解、 字串或會以色彩標示時顯示的控制結構。  
  
 每個**顯示項目**內唯一定義**類別**包含它。 因此，有一個以上**類別**可以有**顯示項目**具有相同名稱。  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage 控制的字型和色彩  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]讓 VSPackages:  
  
-   定義字型和色彩**類別**。  
  
-   指定的字型和色彩用於顯示**顯示項目**。  
  
-   互動**字型和色彩**屬性頁。  
  
-   彙總的多個**類別**分成群組。  
  
-   保留預設設定中的變更。  
  
 有兩種方式互動中的字型和色彩選取[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]。  
  
-   其中一種方式稱為*語法著色*。 它由自訂現有的 VSPackage[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]編輯器，實作語言服務及建立編輯器的來源。  
  
     只有一個**類別**支援這項機制，也就是，**文字編輯器**。  
  
-   一般替代方式支援所有其他**類別**和顯示文字時，在原始檔編輯器以外的使用者介面元件。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>。  
  
## <a name="core-editor-text-settings"></a>核心編輯器的文字設定  
 語言服務物件的核心編輯器的字型和色彩設定都受到**文字 EditorCategory**中找到**顯示設定**的下拉式清單方塊**字型和色彩**屬性頁。  
  
 當使用編輯器，您應該使用的特殊的字型和色彩控制機制，語言服務提供控制及擴充**文字編輯器**設定。 此機制稱為*語法著色*，並提供：  
  
-   簡化的技術來管理的字型和色彩的顯示項目。  
  
     如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 與 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>。  
  
-   完善且最佳化的顏色標示機制。  
  
     如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>。  
  
-   能夠同時使用內建的顯示項目從**文字 EditorCategory**並予以擴充。  
  
     如需詳細資訊，請參閱[How to： 使用內建的色彩項目](../extensibility/internals/how-to-use-built-in-colorable-items.md)和[自訂色彩項目](../extensibility/internals/custom-colorable-items.md)。  
  
-   自動持續性的目前狀態的兩個內建和自訂顯示的項目**文字編輯器**類別目錄。  
  
 如需有關語法著色，請參閱[舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在編輯器中的傳統介面](../extensibility/legacy-interfaces-in-the-editor.md)   
 [舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)