---
title: 實作自訂的分類和顯示項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9593a7addcd9a3f100f45f69e7e692c396e33bfe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-custom-categories-and-display-items"></a>實作自訂的分類和顯示項目
VSPackage 可以提供控制項的字型和色彩，其文字的底部[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 透過自訂的分類和顯示項目。

 自訂的類別和顯示項目位於**字型和色彩**屬性頁。 若要開啟**字型和色彩**屬性頁面上**工具**功能表上，按一下 **選項**。 展開**環境**，然後按一下 **字型和色彩**。

 當使用這項機制，必須實作 Vspackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面和其相關聯的介面。

 基本上，這項機制可以用來修改現有的**顯示項目**和**類別**包含它們。 不過，它不應修改**文字 EditorCategory**或其**顯示項目**。 如需詳細資訊，請參閱[字型和色彩概觀](../extensibility/font-and-color-overview.md)。

 若要實作自訂**類別**或**顯示項目**，VSPackage 必須：

-   建立或識別登錄中的類別。

     IDE 的實作**字型和色彩**屬性頁會使用此資訊正確查詢支援某個的類別的服務。

-   建立或識別登錄中 （選擇性） 的群組。

     這可以用來定義群組代表兩個或多個類別目錄的聯集。 如果定義群組，則 IDE 自動合併子類別目錄，並將發佈群組內的顯示項目。

-   實作 IDE 支援。

-   處理字型和色彩的變更。

 如需資訊，請參閱[存取儲存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。

## <a name="to-create-or-identify-categories"></a>若要建立或識別類別目錄

-   建構一種特殊類型的類別下的登錄項目 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >* \FontAndColors\\`<Category>`]

     *\<類別目錄 >* 為非當地語系化的類別目錄名稱。

-   填入具有兩個值的登錄：

    |名稱|類型|資料|描述|
    |----------|----------|----------|-----------------|
    |分類|REG_SZ|GUID|若要識別類別目錄建立的 GUID。|
    |Package|REG_SZ|GUID|支援類別目錄的 VSPackage 服務的 GUID。|

 在登錄中指定的服務必須提供實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>對應分類。

## <a name="to-create-or-identify-groups"></a>若要建立或識別群組

-   建構一種特殊類型的類別下的登錄項目 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >* \FontAndColors\\  *\<群組 >*]

     *\<群組 >* 為非當地語系化的群組名稱。

-   填入具有兩個值的登錄：

    |名稱|類型|資料|描述|
    |----------|----------|----------|-----------------|
    |分類|REG_SZ|GUID|建立識別群組的 GUID。|
    |Package|REG_SZ|GUID|支援類別目錄服務的 GUID。|

 在登錄中指定的服務必須提供實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>對應的群組。

## <a name="to-implement-ide-support"></a>若要實作 IDE 支援

-   實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>，這會傳回<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>介面或<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>介面，以針對每個 IDE**類別**或群組提供的 GUID。

-   針對每個**類別**它支援、 VSPackage 實作的個別執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>介面。

-   方法實作透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>必須提供此 IDE:

    -   列出的**顯示項目**中**類別目錄。**

    -   可當地語系化名稱**顯示項目**。

    -   顯示每個成員的資訊**類別**。

    > [!NOTE]
    >  每個**類別**必須包含至少一個**顯示項目**。

-   IDE 使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>介面來定義數種類別的聯集。

     它的實作會提供此 IDE:

    -   一份**類別**組成特定的群組。

    -   存取的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>支援每個**類別**群組內。

    -   可當地語系化的群組名稱。

-   正在更新 IDE:

     IDE 會快取資訊的相關**字型和色彩**設定。 因此，在 IDE 的任何修改之後**字型和色彩**組態中，最好也能確保快取最新狀態。

 更新快取透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，並可以執行全域方式或只在選取的項目。

## <a name="to-handle-font-and-color-changes"></a>若要處理的字型和色彩的變更
 若要正確支援 VSPackage 顯示文字的顏色標示，支援 VSPackage 的顏色標示服務必須回應使用者起始所做的變更透過**字型和色彩**屬性頁面。 VSPackage 的做法：

-   藉由實作處理 IDE 所產生的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>介面。

     IDE 呼叫適當的方法，下列的使用者修改**字型和色彩**頁面。 例如，它會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>方法，如果已選取新的字型。

     -或-

-   輪詢變更 IDE。

     這可以透過系統實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。 雖然主要是針對支援的持續性，<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>方法可以用來取得字型和色彩資訊**顯示項目**。 如需詳細資訊，請參閱[存取儲存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。

    > [!NOTE]
    >  為了確保透過輪詢得到的結果正確無誤，可能很有用使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，以判斷是否需要快取排清及更新之前呼叫的方法擷取<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- [取得字型和色彩資訊文字的顏色標示](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [存取預存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)
- [如何： 存取的內建的字型和色彩配置](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)
- [字型和色彩概觀](../extensibility/font-and-color-overview.md)