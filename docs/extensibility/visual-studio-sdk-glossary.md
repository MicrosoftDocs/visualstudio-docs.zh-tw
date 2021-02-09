---
title: Visual Studio SDK 詞彙 |Microsoft Docs
description: 本詞彙提供 Visual Studio SDK 檔中所使用之詞彙的定義。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 707526daaafdbc7e99c11c5b7fb8edf9fdbccc03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925916"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK 詞彙
本詞彙提供檔中使用之詞彙的定義 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 。

## <a name="terms"></a>詞彙
 增益集應用程式、驅動程式或新增至主要應用程式的其他軟體。 在 Visual Studio 整合式開發環境 (IDE) 中，增益集是擴充 IDE 功能的自動化應用程式。

 自動化模型： automation 模型（在舊版 Visual Studio 中已知為擴充性模型）是一種程式設計介面，可讓您存取驅動 IDE 的基礎常式。 增益集、嚮導和宏會使用 automation 模型中的物件來控制或擴充 IDE 的功能。

 GUID 的命令 UI 內容關聯，以及 UI 命令或元素（如工具列）的可見度。 命令 UI 內容與選取內容不同，因為它不會附加至視窗。

 命令 UI 內容可以用來：

- 將 GUID 指派給啟用特定視窗時所出現的工具列。

- 將 GUID 指派給命令的可用性，而不需要載入或執行 VSPackage。

- 指派 GUID 以影響 active key binding。

- 指派 GUID 以開啟宏錄製。

- 指派 GUID 以啟動「偵測模式」，或在編輯器中的「設計」和「執行」模式之間切換。

  元件元件，可以成為應用程式功能的一部分，而不需要應用程式具有軟體執行的任何預先存在資訊。 元件和應用程式之間的通訊只會透過 OLE 樣式介面來進行。

  元件管理員： `SOleComponentManager` 提供最上層元件之非使用者介面協調服務的服務。 服務會實 `SOleComponentManager` 作為 `IOleComponentManager` 介面。

  元件 UI 管理員： `SOleComponentUIManager` 提供使用者介面協調服務的服務。 服務會執行 `SOleComponentUIManager` `IOleComponentUIManager` 和 `IOleInPlaceComponentUIManager` 介面。

  內容包 `IVsUserContext` (COM 物件的物件) 附加至環境元件。 這個物件會保存與元件相關的查閱關鍵字、 **F1** 關鍵字和屬性。 內容包會另外指向任何連結到它們的子上下文包。

  在 IDE 中，內容提供者具有相關聯內容包的元件。 這類元件包括工具視窗、編輯器或專案階層。

  設計工具程式設計介面，可讓使用者管理 UI 的元素 (表單、按鈕和其他控制項) 。

  DocData COM 物件，此物件會封裝世界中檔的基礎資料，其中有檔/視圖分隔 (例如，在文字編輯器的情況下，這會是所有文字編輯器) 的基礎的文字緩衝區。 如果 EditorFactory 未提供此物件，IDE 會代表其製造一個物件。 此物件的責任是管理資料持續性，以及透過相同的多個觀點的共用語義 `DocData` 。 如果 `DocData` 物件支援 `IOleCommandTarget` 介面，則會包含在 UIShell 的命令路由中。

  用來在主機提供的框架內裝載 UI 的 DocObject 技術。 更具體來說，這個詞彙是指支援 `IOleDocument` 和相關介面的任何內嵌。 這項技術有許多潛在的應用程式，例如 COM 檔的執行詳細資料、Visual Basic 5.0 中的工具視窗、Visual Basic 6.0 的 ActiveX 設計工具等等。

  這份檔用來以一般方式參考整份檔，也就是 `DocData` 和 `DocView` 。 例如，DocumentFrame 包含 `DocView` ，但它也會保留的參考 `DocData` 以處理持續性。

  DocView 與使用者互動以查看和操作基礎的 DocObject/內嵌/WindowPane `DocData` 。 使用者不會利用屬於介面設計一部分的檔/視圖分隔 `DocObject` 。 使用者會使用整個 DocObject 來作為一個觀點，而不是使用更抽象的 (以及較不正規化的基礎資料) 概念（稱為） `DocData` 。 `DocView` 物件一律會內嵌在 IDE (MDI 子視窗) 的檔框架物件中。

  DTE `DTE` (開發工具擴充性) 物件是 Visual Studio automation 模型中最上層的存取點，可讓您以程式設計方式自動化和擴充 IDE。

  IDE 所執行的 [動態說明] 視窗工具視窗，並顯示查閱關鍵字或 **F1** 說明主題的清單。

  執行的編輯器程式碼 (類別、CLSID) `DocView` 。 它也 `DocData` 會在支援視圖和資料分離時進行。

  擴充功能，可修改、自訂或新增至 IDE。 您可以使用 automation 模型或 Vspackage 建立延伸模組。

  外部編輯器：並非 IDE 特有的編輯器，例如 Microsoft Word。 它已透過自己的機制註冊，而且可以在 IDE 之外使用。 如果這個編輯器可以內嵌，它就會出現在 IDE 中的視窗內。 如果無法內嵌，則會建立不同的最上層視窗。

  節點的階層樹狀結構，每個節點都與一組屬性相關聯。

  獨立的最上層元件：使用非強制回應最上層視窗的元件，並且可以有效地做為獨立的應用程式視窗運作，但會實作為同進程物件。 因此，獨立的最上層元件必須與 IDE 協調樣式和訊息迴圈服務。 同進程物件沒有自己的訊息迴圈。

  資訊提供者：資訊提供者是一個模組，可查閱關鍵字並以物件的形式傳回主題清單 `IVsUserContextItem` 。 若要提供資訊提供者的 **F1** 和 lookup 關鍵字專案，請將您已編譯的說明檔 (註冊 *。HxS*) 與系統搭配使用。 這些檔案中的說明主題提供 [動態說明] 視窗中顯示的主題清單，並顯示使用者是否按下 **F1**。

  就地元件 VSPackage 物件，它會執行 `IOleInPlaceComponent` 介面來管理以視覺化方式包含在 IDE 所擁有之文件視窗內的視窗。 就地元件不會參與標準的 OLE 功能表合併;相反地，它們會將其使用者介面專案整合到 IDE 中。

  就地元件有兩種類型：寫死就地元件和元件控制項。

  寫死就地元件的功能表、工具列和命令會緊密整合到 IDE 的使用者介面中，如同直接內建在 IDE 中一樣。

  元件控制項沒有任何自己的使用者介面元素會整合到 IDE 中;相反地，它們會使用 IDE 的功能表、命令和工具列。 例如，粗體命令可用來在內嵌于表單中的 rich text 控制項內，以粗體顯示選取的文字。 不過，元件控制項可以要求顯示動態安裝的元件特定 UI 元素。

  language service 一組物件，可讓 VSPackage 開發人員執行電腦語言程式碼編輯器的功能，例如文字標記和標示。

  其他檔案專案專案，用來存放不在任何專案中的開啟檔案。 此專案中的專案清單不會保存。

  專案專案是由階層物件或執行介面的 COM 物件所組成 `IVsHierarchy` 。

  專案特定設計工具或編輯器：無法獨立于專案類型之外使用的設計工具。 所有專案特定設計工具都必須在登錄中輸入其編輯器 Factory 資訊。 當特定的專案中開啟特定檔案類型時，IDE 就可以具現化設計工具。

  專案類型視窗，此視窗會不斷地從全域選取內容中追蹤目前作用中的專案階層和專案。 專案類型的 windows 使用 `SVsTrackSelectionEx` 服務來警示 IDE 的變更，並向使用者顯示意見反應。 方案總管是專案類型視窗的範例。

  屬性視窗先前的屬性瀏覽器。

  參考專案專案，不需要專案的檔案位於相同的目錄中。 相反地，專案本身會儲存並維護其他不相關目錄中的檔案參考。

  執行檔資料表內部結構，IDE 會在此結構中維護所有目前開啟之檔的清單。 此清單包含記憶體中所有開啟的檔，不論目前是否正在編輯檔。 檔是儲存的任何專案，包括在編輯器中開啟的預存程式、專案中的檔案或主要專案檔 (例如 *. vcproj 檔案) 。

  選取範圍內容資料，此資料屬於 IDE 中每一個視窗的詳細資料，而且可用來追蹤使用中的選取專案。 選取範圍內容是由下列專案所組成：

- 專案階層的 `IVsHierarchy` 介面指標

- 專案專案的專案識別碼。

- 介面的指標，可讓您存取使用中 `ISelectionContainer` 物件的屬性。

- 元素值的陣列。

  為位於單一 COM 物件中的一組 COM 介面服務合約。 當您建立由 GUID 所識別的服務時，您會定義一組執行服務的 COM 介面。 COM 物件會使用服務彼此通訊。

  使用者工作所使用之相關專案的方案群組。

  標準設計工具：可以獨立于專案類型使用的設計工具。 所有標準設計工具都必須在登錄中輸入其編輯器 Factory 資訊。 只要開啟具有特定副檔名的檔案，IDE 就可以具現化設計工具。 資料必須保存到檔案中。

  標準編輯器編輯器，可獨立于任何特定專案類型時使用。 這類編輯器已在登錄中註冊 EditorFactories。 這可讓 IDE 找出並叫用編輯器。

  標準 OS 編輯器：不 Visual Studio 特定的內嵌。 它是使用已知的 Win32 金鑰進行註冊 (例如，Win32 Explorer 知道如何叫用) 。 如果可以內嵌這類編輯器，編輯器仍會顯示在 IDE 中的位置。 否則，就會為這類編輯器建立不同的最上層視窗。

  子上下文包 `IVsUserContext` ：連結至內容包的物件。 物件會保存 IDE 元件內選取專案的查閱關鍵字、 **F1** 關鍵字和屬性。 子上下文的範例包括工具視窗中的命令，或編輯器中的關鍵字。

  IDE 所執行的 [工作清單] 工具視窗，並顯示作用中工作的清單。

  物件的文字緩衝區一般名稱 `VSTextBuffer` 。

  物件的文字視圖一般名稱 `VSTextView` 。

  工具最上層元件：以非模式快顯視窗運作的元件，與 IDE 的使用者介面緊密協調。 與獨立的最上層元件相同，工具最上層元件也必須使用 IDE 來協調樣式和訊息迴圈服務。

  最上層元件：管理無模式最上層視窗的 VSPackage 物件，而不是 IDE 視窗的工作區。 最上層元件 `IOleComponent` 會執行介面，以利用訊息迴圈服務，例如存取閒置時間。

  UI 現用： VSPackage 物件，該物件為可見且目前有焦點。

  UI 階層架構，此 COM 物件會執行 `IVsUIHierarchy` 介面以允許顯示階層。 UI 階層視窗 `ISelectionContainer` 會執行介面以更新屬性視窗; 其他專案類型的 windows 則可以視需要使用此實值。

  .VSCT Visual Studio 命令表格。 .Vsct 檔案包含了功能表、工具列和命令的位置和行為的相關資訊（XML 格式）。

  藉由提供下列一或多個專案，VSPackage 可延伸 Visual Studio IDE 的可安裝軟體：使用者介面、服務、專案類型或編輯器/設計工具。 VSPackage 包含的 COM 物件會 `IVsPackage` 執行介面，以及一個或多個其他 com 物件，這些物件會執行其他介面來支援選取專案和其他功能。 此外，VSPackage 具有特定的註冊需求。
