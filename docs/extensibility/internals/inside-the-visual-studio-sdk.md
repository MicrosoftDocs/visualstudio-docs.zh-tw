---
title: 在 Visual Studio SDK 內 |Microsoft Docs
description: 瞭解 Visual Studio SDK 中的擴充功能，包括 Visual Studio 架構、元件、服務、架構和公用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e11ee862f43ead3605d8e07dc159e18da13413b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074700"
---
# <a name="inside-the-visual-studio-sdk"></a>深入探索 Visual Studio SDK

本節提供 Visual Studio 擴充功能的深入資訊，包括 Visual Studio 架構、元件、服務、架構、公用程式等。

## <a name="extensibility-architecture"></a>延伸架構
 下圖顯示 Visual Studio 擴充性架構。 Vspackage 提供應用程式功能，在 IDE 中會以服務的形式共用。 標準 IDE 也提供廣泛的服務，例如 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> ，可讓您存取 IDE 視窗化功能。

 ![環境架構圖形](../../extensibility/internals/media/environment.gif "環境") Visual Studio 架構的一般化視圖

## <a name="vspackages"></a>VSPackages
 VSPackage 是使用 UI 項目、服務、專案、編輯器和設計工具來構成和擴充 Visual Studio 的軟體模組。 Vspackage 是 Visual Studio 的中央架構單位。 如需詳細資訊，請參閱 [VSPackages](../../extensibility/internals/vspackages.md)。

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Visual Studio shell 提供基本功能，並支援其元件 Vspackage 和 MEF 延伸模組之間的交叉通訊。 如需詳細資訊，請參閱 [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)。

## <a name="user-experience-guidelines"></a>使用者體驗指南
 如果您打算設計 Visual Studio 的新功能，您應該看看這些設計和使用性秘訣的指導方針： [Visual Studio 使用者經驗指導方針](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。

## <a name="commands"></a>命令
 命令是完成工作 (例如，列印文件、重新整理檢視，或建立新檔案) 的功能。

 當您擴充 Visual Studio 時，您可以建立命令，並使用 Visual Studio shell 來註冊它們。 您可以指定這些命令在 IDE 中的顯示方式，例如在功能表或工具列上。 一般而言，[**工具**] 功能表上會出現自訂命令，而顯示工具視窗的命令會出現在 [ **View** ] 功能表的 [**其他視窗**] 子功能表上。

 當您建立命令時，您也必須為它建立事件處理常式。 事件處理常式會決定何時可以看見或啟用此命令，讓您修改它的文字，並保證命令在啟用時適當地回應。 在大部分的情況下，IDE 會使用介面來處理命令 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。 Visual Studio 中的命令會從最內層的命令內容開始處理，根據本機選取專案，然後根據全域選取專案繼續進行最外層的內容。 加入主功能表的命令可立即用於指令碼編寫。

 如需詳細資訊，請參閱 [命令、功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)。

## <a name="menus-and-toolbars"></a>功能表和工具列
 功能表和工具列提供使用者叫用命令的方法。 功能表是命令的資料列或資料行，通常會在工具視窗的頂端顯示為個別的文字專案。 子功能表是使用者按一下包含小箭號的命令時所顯示的次要功能表。 當使用者以滑鼠右鍵按一下特定的 UI 專案時，就會顯示內容功能表。 某些常用的功能表名稱 **是 [** 檔案]、[ **編輯**]、[ **視圖**] 和 [ **視窗]**。 如需詳細資訊，請參閱 [擴充功能表和命令](../../extensibility/extending-menus-and-commands.md)。

 工具列是按鈕和其他控制項的資料列或資料行，例如下拉式方塊、清單方塊和文字方塊。 工具列按鈕通常有圖示影像，例如 [ **開啟** 檔案] 命令的資料夾圖示或 **列印** 命令的印表機。 所有工具列元素都會與命令相關聯。 當您按一下工具列按鈕時，會執行其相關聯的命令。 在下拉式控制項的案例中，下拉式清單中的每個專案都會與不同的命令相關聯。 某些工具列控制項（例如分隔器控制項）為混合。 控制項的一端是工具列按鈕，另一端則是向下箭號，可在按一下時顯示數個命令。

## <a name="tool-windows"></a>工具視窗
 在 IDE 中使用工具視窗來顯示資訊。 [**工具箱**]、[**方案總管**]、[**屬性**] 視窗和 [**網頁瀏覽器**] 都是工具視窗的範例。

 工具視窗通常會提供使用者可互動的各種控制項。 例如，[ **屬性** ] 視窗可讓使用者設定物件的屬性，以提供特定用途。 [ **屬性** ] 視窗是以這種方式特製化，但也是一般的，因為它可以在許多不同的情況下使用。 同樣地， **輸出** 視窗是特製化的，因為它會提供以文字為基礎的輸出，但一般是因為 Visual Studio 中有許多子系統可以使用它來提供輸出給 Visual Studio 的使用者。

 請考慮下圖中的 Visual Studio，其中包含數個工具視窗：

 ![螢幕擷取畫面](../../extensibility/internals/media/t1gui.png "T1gui")

 部分工具視窗會停駐在單一窗格上，顯示方案總管的工具視窗，並隱藏其他工具視窗，但按一下索引標籤可讓他們使用。 此圖顯示兩個其他工具視窗、[ **錯誤清單** ] 和 [ **輸出** ] 視窗，並在單一窗格上停駐在一起。

 另外也會顯示主文件窗格，其中顯示數個編輯器視窗。 雖然工具視窗通常只有一個實例 (例如，您只能開啟一個 **方案總管**) 、編輯器視窗可以有多個實例，而每個實例都是用來編輯個別的檔，但全都停駐在相同的窗格中。 圖片會顯示具有兩個編輯器視窗的 [檔] 窗格，一個表單設計工具視窗。 [檔] 窗格中的所有視窗都可以藉由按一下 [tab] 來使用，但是包含 EditorPane .cs 檔案的 [編輯器] 視窗是可見的，而且是使用中的。

 當您延伸 Visual Studio 時，您可以建立可讓 Visual Studio 使用者與您的延伸模組互動的工具視窗。 您也可以建立自己的編輯器，讓 Visual Studio 使用者編輯檔。 由於您的工具視窗和編輯器將會整合到 Visual Studio 中，因此您不需要進行程式設計，就能將它們固定或顯示在索引標籤上。 當這些使用者在 Visual Studio 中正確註冊時，就會在 Visual Studio 中自動擁有工具視窗和文件視窗的一般功能。 如需詳細資訊，請參閱 [擴充和自訂工具視窗](../../extensibility/extending-and-customizing-tool-windows.md)。

## <a name="document-windows"></a>文件視窗
 文件視窗是多重文件介面的框架子視窗， (MDI) 視窗。 文件視窗通常是用來裝載文字編輯器、表單編輯器 (也稱為設計工具) 或編輯控制項，但它們也可以裝載其他功能類型。 [ **新增** 檔案] 對話方塊包含 Visual Studio 提供的文件視窗範例。

 大部分的編輯器都是程式設計語言或檔案類型的特定語言，例如 HTML 網頁、框架、c + + 檔案或標頭檔。 藉由在 [ **新增** 檔案] 對話方塊中選取範本，使用者會針對與範本相關聯的檔案類型，以動態方式建立編輯器的文件視窗。 當使用者開啟現有的檔案時，也會建立文件視窗。

 文件視窗僅限 MDI 工作區。 每一個文件視窗的頂端都有一個索引標籤，而且定位順序會連結至可能在 MDI 區域中開啟的其他視窗。 在文件視窗的索引標籤上按一下滑鼠右鍵，會顯示快捷方式功能表，其中包含將 MDI 區域分割成多個水準或垂直索引標籤群組的選項。 分割 MDI 區域可同時查看多個檔案。 如需詳細資訊，請參閱 [文件視窗](../../extensibility/internals/document-windows.md)。

## <a name="editors"></a>編輯器
 Visual Studio 編輯器可讓您自訂它，並透過 Managed Extensibility Framework (MEF) ，將它用於您自己的內容類型。 在許多情況下，您不需要建立 VSPackage 來延伸編輯器，不過如果您想要從 shell 包含功能 (例如，) 的功能表命令或快速鍵，則可以將 MEF 擴充功能與 VSPackage 結合。

 您也可以建立自訂編輯器，例如，如果您想要讀取和寫入資料庫，或是想要使用設計工具。 您也可以使用外部編輯器，例如 [記事本] 或 Microsoft WordPad。 如需詳細資訊，請參閱 [編輯器和語言服務延伸](../../extensibility/editor-and-language-service-extensions.md)。

## <a name="language-services"></a>語言服務
 如果您希望 Visual Studio 編輯器支援新的程式設計關鍵字或甚至是新的程式設計語言，您可以建立語言服務。 每個語言服務都可以完全、部分或完全不執行某些編輯器功能。 根據其設定方式，語言服務可以在編輯器中提供語法醒目提示、括弧對稱、IntelliSense 支援和其他功能。

 語言服務的核心是剖析器和掃描器。 掃描器 (或詞法分析) 會將原始程式檔分割成稱為權杖的元素，而剖析器會在這些標記之間建立關聯性。 當您建立語言服務時，您必須執行剖析器和掃描器，讓 Visual Studio 可以瞭解語言的標記和文法。 您可以建立受控或非受控語言服務。 如需詳細資訊，請參閱 [舊版語言服務](../../extensibility/internals/legacy-language-service-extensibility.md)的擴充性。

## <a name="projects"></a>專案

在 Visual Studio 中，專案是開發人員用來組織和建立原始程式碼和其他資源的容器。 專案可讓您組織、建立、偵測和部署原始程式碼、Web 服務和資料庫的參考，以及其他資源。 Vspackage 可以藉由提供專案類型、專案子類型和自訂工具來延伸 Visual Studio 的專案系統。

專案也可以一起收集在一個 *方案* 中，也就是一或多個專案的群組，這些專案會一起運作來建立應用程式。 與解決方案相關的專案和狀態資訊會儲存在兩個方案檔中，以文字為基礎的 [方案 ( .sln) ](solution-dot-sln-file.md) 檔和二進位 [方案使用者選項 ( .suo) ](solution-user-options-dot-suo-file.md)檔。 這些檔案類似于舊版 Visual Basic 所使用的 ( vbg) 檔案，以及工作區 (. dsw) 和 [使用者選項] () 在舊版 c + + 中使用的檔案。

如需詳細資訊，請參閱 [專案](../../extensibility/internals/projects.md) 和 [方案](../../extensibility/internals/solutions-overview.md)。

## <a name="project-and-item-templates"></a>專案與項目範本
 Visual Studio 包括預先定義的專案範本和專案專案範本。 您也可以建立自己的範本，或從社區取得範本，然後將其整合至 Visual Studio。 [MSDN 程式碼庫](https://code.msdn.microsoft.com/site/search?query=visual%20studio)是範本和延伸模組的起點。

 範本包含建立特定類型的應用程式、控制項、程式庫或類別所需的專案結構和基本檔案。 當您想要開發類似于其中一個範本的軟體時，請建立以範本為基礎的專案，然後修改該專案中的檔案。

> [!NOTE]
> 專案不支援此範本架構 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 。

 如需詳細資訊，請參閱 [加入專案和專案專案範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

## <a name="properties-and-options"></a>屬性和選項
 [ **屬性** ] 視窗會顯示單一或多個選取專案的屬性： [ [擴充屬性](../../extensibility/internals/extending-properties.md) 選項] 頁面包含與特定元件相關的選項組，例如程式設計語言或 VSPackage： [ [選項] 和 [選項] 頁面](../../extensibility/internals/options-and-options-pages.md)。 設定通常是可匯入和匯出的 UI 相關功能： [使用者設定的支援](../../extensibility/internals/support-for-user-settings.md)。

## <a name="visual-studio-services"></a>Visual Studio 服務
 服務會提供一組特定的介面供元件取用。 Visual Studio 提供一組可供任何元件（包括延伸模組）使用的服務。 例如，Visual Studio services 可讓您以動態方式顯示或隱藏工具視窗，讓您能夠存取說明、狀態列或 UI 事件。 Visual Studio 編輯器也提供可由編輯器延伸模組匯入的服務。 如需詳細資訊，請參閱 [使用和提供服務](../../extensibility/using-and-providing-services.md)。

## <a name="debugger"></a>偵錯工具
 偵錯工具是語言特定的偵錯工具元件的使用者介面。 如果您已建立新的語言服務，則必須建立特定的 debug engine 以連結至偵錯工具。 如需詳細資訊，請參閱 [Visual Studio 偵錯工具](../../extensibility/debugger/visual-studio-debugger-extensibility.md)擴充性。

## <a name="source-control"></a>原始檔控制
 如需有關執行原始檔控制外掛程式或 VSPackage 的詳細資訊，請參閱 [原始檔控制](../../extensibility/internals/source-control.md)。

## <a name="wizards"></a>精靈
 您可以建立一個與新的專案類型搭配使用的 wizard，讓您的使用者可以在建立該類型的新專案時，協助使用者做出正確的決策。 如需詳細資訊，請參閱 [嚮導](../../extensibility/internals/wizards.md)。

## <a name="custom-tools"></a>自訂工具
 自訂工具可讓您將工具與專案中的專案建立關聯，並在儲存檔案時執行該工具。 如需詳細資訊，請參閱 [自訂工具](../../extensibility/internals/custom-tools.md)。

## <a name="vssdk-utilities"></a>VSSDK 公用程式
 VSSDK 包含一組公用程式，您可能需要這些公用程式才能使用 Vspackage 的不同層面。 如需詳細資訊，請參閱 [VSSDK 公用程式](../../extensibility/internals/vssdk-utilities.md)。

## <a name="using-windows-installer"></a>使用 Windows Installer
 在某些情況下，您可能需要使用 Windows Installer 而不是 VSIX 安裝程式：例如，您可能需要寫入登錄。 如需搭配使用 Windows Installer 與擴充功能的相關資訊，請參閱使用 [Windows Installer 安裝 vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)。

## <a name="help-viewer"></a>說明檢視器
 您可以將自己的說明和 F1 頁面整合到說明檢視器中。 如需詳細資訊，請參閱 [MICROSOFT HELP VIEWER SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)。
