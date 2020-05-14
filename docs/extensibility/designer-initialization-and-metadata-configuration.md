---
title: 設計器初始化和中繼資料設定 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712218"
---
# <a name="designer-initialization-and-metadata-configuration"></a>設計器初始化與中繼資料設定

操作與設計器或設計器元件關聯的中繼資料和篩選器屬性為應用程式提供了一種機制,用於定義特定設計器在設計器可用時使用哪些<xref:System.Type>工具來處理不同的物件(如資料結構、類或圖形實體),以及 Visual Studio IDE 如何配置為支援設計器(例如,可用的**工具箱**類別或選項卡)。

提供了[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]幾種機制,便於控制設計器或設計器元件的初始化,並通過 VSPackage 操作其元數據。

## <a name="initialize-metadata-and-configuration-information"></a>初始化中繼資料和設定資訊
 由於它們是按需載入的,因此在設計器實例化之前,Visual Studio 環境可能尚未載入 VSPackages。 因此,VSPackages 不能使用標準機制在創建時配置設計器或設計器元件,即處理<xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>事件。 相反,VSPackage<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>實現 介面的實例並註冊自身以提供自定義項,稱為設計曲面擴展。

### <a name="customize-initialization"></a>自訂初始化

自訂設計器、元件或設計器表面涉及:

1. 修改設計器中繼資料並有效更改存取<xref:System.Type>或轉換某個特定內容的方式。

    這通常是通過<xref:System.Drawing.Design.UITypeEditor><xref:System.ComponentModel.TypeConverter>或機制完成的。

    例如,當初始<xref:System.Windows.Forms>化基於的設計人員時,Visual Studio 環境<xref:System.Drawing.Design.UITypeEditor><xref:System.Web.UI.WebControls.Image>將修改與設計器一起使用的物件,以使用資源管理器獲取位圖而不是檔案系統。

2. 通過訂閱事件或獲取專案配置資訊來與環境集成。 您可以通過<xref:System.ComponentModel.Design.ITypeResolutionService>獲取 介面獲取專案設定資訊並訂閱事件。

3. 通過啟動適當的**工具箱**類別或通過將類的實例應用於設計器來限制設計器的適用<xref:System.ComponentModel.ToolboxItemFilterAttribute>性來 修改使用者環境。

### <a name="designer-initialization-by-a-vspackage"></a>按 VSPackage 初始化設計器

VSPackage 應按以下操作處理設計器初始化:

1. 創建實現<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>類的物件。

   > [!NOTE]
   > 不應<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>在類的同一對象<xref:Microsoft.VisualStudio.Shell.Package>上實現 類。

2. 註冊實現<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>為 VSPackage 的設計器擴展提供支援的類。 用<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>應用程式的實體來註冊<xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>類別,<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>並註冊提供 VSPackage 的<xref:Microsoft.VisualStudio.Shell.Package>類別 。

每當創建設計器或設計器元件時,可視化工作室環境:

- 訪問每個已註冊的設計曲面擴展提供程式。

- 實例化和初始化每個設計曲面擴展提供程式物件的<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>實例。

- 調用每個設計曲面擴展提供程式<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>的方法<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>或 方法(視適用)。

當作為<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>VSPackage 的成員實現該物件時,請務必瞭解:

- Visual Studio 環境不提供`DesignSurfaceExtension`對特定 提供程式修改的元數據或其他配置設置的任何控制。 兩個或多個`DesignSurfaceExtension`提供程式可能會以衝突的方式修改同一設計器功能,最終修改是決定性的。 最後應用的是哪個修改是不確定的。

- 通過將 物件<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension><xref:System.ComponentModel.ToolboxItemFilterAttribute>的 實例應用於該實現,可以顯式將對象的實現限制為特定設計器。 有關**工具箱**項目篩選的詳細資訊,請參閱<xref:System.ComponentModel.ToolboxItemFilterAttribute><xref:System.ComponentModel.ToolboxItemFilterType>與 。

## <a name="additional-metadata-provisioning"></a>其他中繼資料預先配

VSPackage 可以更改設計器或設計器元件的配置,而不是在設計時。

類<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>可以以程式設計方式使用,也可以應用於提供設計器的 VSPackage。

<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>類的實例用於修改在設計圖面上創建的元件的元數據。 例如,可以將<xref:System.Windows.Forms.CommonDialog>物件使用的預設屬性瀏覽器替換為自定義屬性瀏覽器。

套用於 VSPackage 實現<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>的<xref:Microsoft.VisualStudio.Shell.Package>實體提供的修改 可以具有兩個作用域之一:

- 全域 ─ 給定元件的所有新實體

- 本地 - 僅與目前 VSPackage 提供的設計表面上創建的元件實例相關。

應用於`IsGlobal`VSPackage<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>實現 的實體<xref:Microsoft.VisualStudio.Shell.Package>屬性 決定了此範圍。

<xref:Microsoft.VisualStudio.Shell.Package>將屬性應用於<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A><xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>物件 屬性`true`設置為的實現,如下所示,將更改整個 Visual Studio 環境的瀏覽器:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

如果全域旗標設定為`false`,則中繼資料變更是目前 VSPackage 支援的目前設計器的本地:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> 設計圖面僅支援創建元件,因此只有元件可以具有本地元數據。 在上面的示例中,我們嘗試修改屬性,例如物件`Color`的屬性。 如果`false`為全域標誌傳入,`CustomBrowser`則永遠不會出現,因為設計器從未實際創建`Color`的實例。 將全域標誌`false`設置為對元件(如控件、計時器和對話框)很有用。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [延伸設計時支援](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
