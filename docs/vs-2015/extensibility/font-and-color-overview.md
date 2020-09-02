---
title: 字型和色彩總覽 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204355"
---
# <a name="font-and-color-overview"></a>字型和色彩概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題討論 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (IDE) 整合式開發環境中的文字字型和色彩設定。 它也會介紹類別和顯示專案的概念，並說明 Vspackage 和核心編輯器如何使用文字屬性。  
  
## <a name="the-fonts-and-colors-property-page"></a>[字型和色彩] 屬性頁  
 您可以 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 透過 [字型 **和色彩** ] 屬性頁，在整合式開發環境中管理所顯示文字的屬性 (IDE) 。 若要尋找 [字型 **和色彩** ] 屬性頁，請按一下 [ **工具** ] 功能表上的 [ **選項**]。 展開 [環境]****，再按一下 [字型和色彩]****。  
  
## <a name="categories-and-display-items"></a>類別和顯示專案  
 字型和色彩會組織成 **類別** 和 **顯示專案**。  
  
- **類別**是許多**顯示專案**的邏輯或功能容器。  
  
   **類別**清單位於 [字型**和色彩**] 屬性頁的 [**顯示設定**] 下拉式清單方塊中。  
  
- **顯示專案**是定義完善的文字實體，例如批註、字串或顯示時要以色彩標示的控制項結構。  
  
  每個 **顯示專案** 都是在包含它的 **類別** 中唯一定義。 因此，一個以上的 **類別目錄** 可以有相同名稱的 **顯示專案** 。  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage 控制項的字型和色彩  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]允許 vspackage：  
  
- 定義字型和色彩 **類別**。  
  
- 指定用來顯示 **顯示專案**的字型和色彩。  
  
- 與 [字型 **和色彩** ] 屬性頁互動。  
  
- 將多個 **類別** 匯總成群組。  
  
- 保存預設設定中的變更。  
  
  有兩種方式可以與中的字型和色彩選項互動 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 。  
  
- 其中一種方式稱為 *語法著色*。 它是由自訂現有 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 編輯器來執行語言服務和建立來源編輯器的 VSPackage 所使用。  
  
   只有一個 **類別** 支援這項機制，也就是 **文字編輯器**。  
  
- 在顯示文字時，更一般的替代方案支援來源編輯器以外的其他所有 **類別** 和使用者介面元件。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>。  
  
## <a name="core-editor-text-settings"></a>核心編輯器文字設定  
 語言服務物件之核心編輯器的字型和色彩設定，是由 [字型**和色彩**] 屬性頁的 [**顯示設定**] 下拉式清單方塊中找到的**文字 EditorCategory**所控管。  
  
 使用編輯器時，您應該使用語言服務提供的特殊字型和色彩控制機制來控制及擴充 **文字編輯器** 設定。 此機制稱為 *語法著色* ，並提供：  
  
- 管理顯示專案字型和色彩的簡化技術。  
  
   如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>。  
  
- 定義完善且優化的顏色標示機制。  
  
   如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>。  
  
- 這兩種功能都可以使用內建的 **文字 EditorCategory** 顯示專案並加以擴充。  
  
   如需詳細資訊，請參閱 [如何：使用內建的可設定色彩專案](../extensibility/internals/how-to-use-built-in-colorable-items.md) 和 [自訂可設定色彩專案](../extensibility/internals/custom-colorable-items.md)。  
  
- 自動將內建和自訂顯示專案的目前狀態與 **文字編輯器** 分類保持在一起。  
  
  如需語法著色的詳細資訊，請參閱 [舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編輯器中的舊版介面](../extensibility/legacy-interfaces-in-the-editor.md)   
 [舊版語言服務中的語法著色](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
