---
title: 在可視化工作室 SDK 中 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707578"
---
# <a name="inside-the-visual-studio-sdk"></a>深入探索 Visual Studio SDK

本節提供有關 Visual Studio 擴展的深入資訊,包括 Visual Studio 體系結構、元件、服務、架構、實用程式等。

## <a name="extensibility-architecture"></a>可擴充性架構
 下圖顯示了可視化工作室擴展性體系結構。 VS包提供應用程式功能,這些功能在IDE之間作為服務共用。 標準 IDE 還提供廣泛的服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>,例如 ,這些服務提供對 IDE 視窗功能的訪問。

 ![環境結構圖形](../../extensibility/internals/media/environment.gif "Environment")視覺化工作室架構的廣義視圖

## <a name="vspackages"></a>VSPackages
 VSPackage 是使用 UI 項目、服務、專案、編輯器和設計工具來構成和擴充 Visual Studio 的軟體模組。 VS包是視覺工作室的中心建築單元。 如需詳細資訊，請參閱 [VSPackages](../../extensibility/internals/vspackages.md)。

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Visual Studio 外殼提供基本功能,並支援其元件 VSPackages 和 MEF 擴充之間的交叉通信。 有關詳細資訊,請參閱[可視化工作室外殼](../../extensibility/internals/visual-studio-shell.md)。

## <a name="user-experience-guidelines"></a>使用者體驗指南
 如果您計劃為 Visual Studio 設計新功能,您應該查看這些設計和可用性提示指南:[視覺化工作室使用者體驗指南](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。

## <a name="commands"></a>命令
 命令是完成工作 (例如，列印文件、重新整理檢視，或建立新檔案) 的功能。

 擴展可視化工作室時,您可以創建命令並將其註冊到可視化工作室外殼。 您可以指定這些命令在 IDE 中的顯示方式,例如,在功能表或工具列上。 通常,「**工具**」功能表上會出現自訂命令,用於顯示工具視窗的命令將顯示在 **「視圖」** 選單**的其他 Windows**子選單上。

 建立命令時,還必須為其創建事件處理程式。 事件處理程式確定命令何時可見或啟用,允許您修改其文本,並保證命令在啟動時做出適當的回應。 在大多數情況下,IDE<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>使用介面處理命令。 Visual Studio 中的命令從最裡面的命令上下文開始處理,基於本地選擇,並根據全域選擇進入最外層上下文。 加入主功能表的命令可立即用於指令碼編寫。

 有關詳細資訊,請參閱[命令、選單和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="menus-and-toolbars"></a>選單和工具列
 功能表和工具列為使用者提供調用命令的方法。 選單是命令的行或列,通常顯示為工具視窗頂部的單個文本項。 子功能表是輔助功能表,當用戶單擊包含小箭頭的命令時顯示。 當使用者右鍵單擊某些UI元素時,將顯示上下文菜單。 一些常見的選單名稱是**檔案**、**編輯**、**檢視**與**視窗**。 有關詳細資訊,請參閱[延伸選單和指令](../../extensibility/extending-menus-and-commands.md)。

 工具列是按鈕和其他控制項的行或列,如組合框、清單框和文字框。 工具列按鈕通常具有圖示影像,例如 **「打開檔案」** 命令的資料夾圖示或 **「列印」** 指令的印表機。 所有工具列元素都與命令相關聯。 按一下工具列按鈕時,將運行其關聯的命令。 對於下拉控制件,下拉清單中的每個項都與不同的命令相關聯。 某些工具列控制件(如拆分器控制項)是混合控制件。 控件的一側是工具列按鈕,另一邊是向下箭頭,按一下時顯示多個命令。

## <a name="tool-windows"></a>工具視窗
 在 IDE 中使用工具視窗來顯示資訊。 **工具箱**、**解決方案資源管理員**、**屬性**視窗和**Web 瀏覽器**是工具視窗的範例。

 工具視窗通常提供各種控制項,用戶可以與之互動。 例如,「**屬性」** 視窗允許用戶設置用於特定用途的物件的屬性。 **屬性**視窗在此意義上是專門化的,但也具有常規性,因為它可用於許多不同的情況。 同樣,**輸出**視窗是專門化的,因為它提供基於文本的輸出,但一般,因為 Visual Studio 中的許多子系統可以使用它向 Visual Studio 使用者提供輸出。

 請考慮以下 Visual Studio 圖片,其中包含多個工具視窗:

 ![螢幕擷取畫面](../../extensibility/internals/media/t1gui.png "T1gui")

 某些工具視窗停靠在一個窗格中,該窗格顯示解決方案資源管理器工具視窗並隱藏其他工具視窗,但通過按一下選項卡使其可用。 圖片顯示另外兩個工具視窗,**錯誤列表**和**輸出**視窗,停靠在單個窗格上。

 還顯示的是主文檔窗格,它顯示了多個編輯器視窗。 儘管工具視窗通常只有一個實例(例如,您只能打開一個**解決方案資源管理器**),但編輯器視窗可以有多個實例,每個實例都用於編輯單獨的文檔,但所有這些實例都停靠在同一窗格中。 圖片顯示的文檔窗格,該窗格具有兩個編輯器視窗,一個窗體設計器視窗。 通過單擊選項卡,文檔窗格中的所有視窗都可用,但包含EditorPane.cs檔的編輯器窗口可見且處於活動狀態。

 擴展 Visual Studio 時,您可以建立工具視窗,讓 Visual Studio 使用者與您的擴充進行互動。 您還可以創建自己的編輯器,讓 Visual Studio 使用者編輯文檔。 由於工具視窗和編輯器將整合到 Visual Studio 中,因此您不必對其進行程式設計才能正確停靠或顯示在選項卡上。 當它們在 Visual Studio 中正確註冊時,它們將自動具有 Visual Studio 中工具視窗和文檔視窗的典型功能。 有關詳細資訊,請參閱[延伸並自訂工具視窗](../../extensibility/extending-and-customizing-tool-windows.md)。

## <a name="document-windows"></a>文件視窗
 文件視窗是多文檔介面 (MDI) 視窗的帶框子視窗。 文件視窗通常用於承載文本編輯器、表單編輯器(也稱為設計器)或編輯控制項,但它們還可以承載其他功能類型。 "**新增檔案**"對話框包括 Visual Studio 提供的文件視窗範例。

 大多數編輯器特定於程式設計語言或檔類型,如 HTML 頁、框架集、C++檔或標頭檔。 通過在 **「新建檔案」** 對話方塊中選擇範本,使用者會動態地為與範本關聯的檔案類型的編輯器創建文件視窗。 當使用者打開現有檔時,也會創建文檔視窗。

 文檔視窗僅限於 MDI 工作區。 每個文件視窗的頂部都有一個選項卡,選項卡順序連結到 MDI 區域中可能打開的其他視窗。 右鍵按一下文件視窗的選項卡將顯示一個快捷方式選單,其中包含將 MDI 區域拆分為多個水準或垂直選項卡組的選項。 分割 MDI 區域可同時查看多個檔案。 有關詳細資訊,請參考[文件視窗](../../extensibility/internals/document-windows.md)。

## <a name="editors"></a>編輯器
 Visual Studio 編輯器允許您自定義它,並透過託管擴充性框架 (MEF) 將其用於您自己的類型的內容。 在許多情況下,您不需要創建 VSPackage 來擴展編輯器,儘管如果要包括 shell 中的要素(例如,選單命令或快捷鍵),則可以將 MEF 擴展與 VSPackage 合併。

 您還可以創建自定義編輯器,例如,如果要讀取和寫入資料庫,或者希望使用設計器。 您還可以使用外部編輯器(如記事本或微軟 WordPad)。 有關詳細資訊,請參閱[編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。

## <a name="language-services"></a>語言服務
 如果希望 Visual Studio 編輯器支援新的程式設計關鍵字,甚至支援新的程式設計語言,則可以創建語言服務。 每個語言服務可以完全、部分或根本不實現某些編輯器功能。 根據配置方式,語言服務可以在編輯器中提供語法突出顯示、大括弧匹配、IntelliSense 支援和其他功能。

 語言服務的核心是解析器和掃描器。 掃描程式(或 lexer)將源檔劃分為稱為令牌的元素,解析器在這些權杖之間建立關係。 創建語言服務時,必須實現解析器和掃描器,以便 Visual Studio 能夠理解該語言的權杖和語法。 您可以建立託管或非託管語言服務。 有關詳細資訊,請參閱[舊語言服務擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)。

## <a name="projects"></a>專案

在 Visual Studio 中,專案是開發人員用於組織和構建原始碼和其他資源的容器。 項目允許您組織、構建、除錯和部署原始碼、對 Web 服務和資料庫的引用以及其他資源。 VSPackages 可以通過提供項目類型、專案子類型和自定義工具來擴展 Visual Studio 專案系統。

專案也可以聚集在一個解決方案中,該*解決方案*是由一個或多個項目組成的分組,它們協同工作以創建應用程式。 與解決方案相關的項目和狀態資訊儲存在兩個解決方案檔中,即基於文本[的解決方案 (.sln) 檔案和](solution-dot-sln-file.md)二進位[解決方案使用者選項 (.suo) 檔案](solution-user-options-dot-suo-file.md)。 這些文件類似於早期版本的 Visual Basic 中使用的群組 (.vbg) 檔案,以及用於早期版本的 C++的工作區 (.dsw) 和使用者選項 (.opt) 檔。

有關詳細資訊,請參閱[專案和](../../extensibility/internals/projects.md)[解決方案](../../extensibility/internals/solutions-overview.md)。

## <a name="project-and-item-templates"></a>專案與項目範本
 可視化工作室包括預定義的專案範本和專案專案範本。 您還可以製作自己的範本或從社區獲取範本,然後將它們集成到 Visual Studio 中。 [MSDN 程式庫](https://code.msdn.microsoft.com/site/search?query=visual%20studio)是獲取範本和擴展的地方。

 樣本包含生成特定類型的應用程式、控制項、庫或類所需的專案結構和基本檔。 當您要開發類似於其中一個範本的軟體時,請創建基於範本的專案,然後修改該專案中的檔。

> [!NOTE]
> [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案不支援此範本體系結構。

 有關詳細資訊,請參閱[新增專案和專案項目樣本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

## <a name="properties-and-options"></a>屬性與選項
 屬性**視窗**顯示單個或多個選取的屬性:[延伸屬性](../../extensibility/internals/extending-properties.md)選項頁包含與特定元件相關的選項集,如程式設計語言或 VSPackage:[選項與選項頁](../../extensibility/internals/options-and-options-pages.md)。 設定通常是可以匯入與匯出的與 UI 相關的功能:[支援使用者設定](../../extensibility/internals/support-for-user-settings.md)。

## <a name="visual-studio-services"></a>視覺工作室服務
 服務為元件提供一組特定的介面。 Visual Studio 提供一組服務,這些服務可用於任何元件(包括擴展)。 例如,Visual Studio 服務允許動態顯示或隱藏工具視窗,啟用對幫助、狀態列或 UI 事件的訪問。 Visual Studio 編輯器還提供可由編輯器擴展導入的服務。 有關詳細資訊,請參閱[使用和提供服務](../../extensibility/using-and-providing-services.md)。

## <a name="debugger"></a>偵錯工具
 除錯器是特定於語言的除錯元件的使用者介面。 如果已創建新的語言服務,則需要創建特定的調試引擎以掛接到調試器。 有關詳細資訊,請參閱[可視化工作室調試器擴展性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)。

## <a name="source-control"></a>原始程式碼控制
 有關實現原始碼管理外掛程式或 VSPackage 的資訊,請參考[原始碼管理](../../extensibility/internals/source-control.md)。

## <a name="wizards"></a>精靈
 您可以結合新的項目類型創建嚮導,以便向導可幫助使用者在創建該類型的新專案時做出正確的決策。 有關詳細資訊,請參閱[精靈](../../extensibility/internals/wizards.md)。

## <a name="custom-tools"></a>自訂工具
 自定義工具允許您將工具與專案中的項目相關聯,並在保存檔時運行該工具。 有關詳細資訊,請參閱[自訂工具](../../extensibility/internals/custom-tools.md)。

## <a name="vssdk-utilities"></a>VSSDK 公用程式
 VSSDK 包括一組實用程式,您可能需要這些實用程式才能處理 VSPackages 的不同方面。 有關詳細資訊,請參閱[VSSDK 公用程式](../../extensibility/internals/vssdk-utilities.md)。

## <a name="using-windows-installer"></a>使用 Windows 安裝程式
 在某些情況下,您可能需要使用 Windows 安裝程式而不是 VSIX 安裝程式:例如,您可能需要寫入註冊表。 有關將 Windows 安裝程式與延伸一起使用的資訊,請參閱[使用 Windows 安裝程式安裝 VS 程式](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。

## <a name="help-viewer"></a>說明檢視器
 您可以將自己的説明和 F1 頁面整合到幫助查看器中。 有關詳細資訊,請參閱[Microsoft 說明檢視器 SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)。
