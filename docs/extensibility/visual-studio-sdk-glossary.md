---
title: Visual Studio SDK 詞彙 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a08985c4977896e35fa8cd94014385ac32dd8bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148895"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK 詞彙
僅提供所用的詞彙定義[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]文件。  
  
## <a name="terms"></a>詞彙  
 Add-In - 增益集  
 公用程式的應用程式、 驅動程式或加入至主應用程式的其他軟體。 在 Visual Studio 整合式的開發環境 (IDE) 中，增益集是自動化的應用程式，擴充 IDE 功能。  
  
 Automation 模型  
 Automation 模型，在舊版的 Visual Studio 擴充性模型，以得知是程式設計介面，可讓您存取的基礎常式 IDE 該磁碟機。 增益集、 精靈和巨集使用 automation 模型來控制中的物件或擴充 IDE 功能。  
  
 命令 UI 內容  
 UI 的命令或工具列等項目的可見性與 GUID 的關聯。 命令 UI 內容是與選取範圍內容不同，因為它並未附加至視窗。  
  
 命令 UI 內容可用來：  
  
-   將 GUID 指派給特定的視窗啟動時出現的工具列。  
  
-   指派給命令的可用性的 GUID，而不必載入或執行 VSPackage。  
  
-   指派會影響使用中的索引鍵繫結的 GUID。  
  
-   指派 GUID，以開啟 巨集錄製。  
  
-   指派的 GUID，可啟用偵錯模式，或設計與在編輯器中的執行的模式之間切換。  
  
 元件  
 不需要預先存在的任何資訊的軟體實作該應用程式可以建立應用程式的功能的一部分的軟體的部分。 元件和應用程式之間的通訊是等作業只透過 OLE 樣式介面。  
  
 元件管理員  
 服務， `SOleComponentManager`，這樣會提供最上層元件的非使用者介面協調服務。 `SOleComponentManager`服務實作`IOleComponentManager`介面。  
  
 元件 UI 管理員  
 服務， `SOleComponentUIManager`，這樣會提供使用者介面協調服務。 `SOleComponentUIManager`服務實作`IOleComponentUIManager`和`IOleInPlaceComponentUIManager`介面。  
  
 內容包  
 `IVsUserContext`物件 （COM 物件） 附加至環境元件。 此物件會保存查詢關鍵字、 F1 關鍵字和相關元件的屬性。 此外，內容包點來連結至其任何子內容包。  
  
 內容提供者  
 在 IDE 具有與其相關聯的內容封包的元件。 這類元件加入工具視窗、 編輯器或專案階層架構。  
  
 設計工具  
 程式設計介面，可讓使用者管理的使用者介面 （form、 按鈕和其他控制項） 的項目。  
  
 DocData  
 COM 物件，封裝的世界中的文件的基礎資料的文件/檢視表的分隔 （例如，在文字編輯器案例中，為基礎的所有文字編輯器檢視的文字緩衝）。 如果 EditorFactory 未提供此物件，IDE 會製造代替它的其中一個。 此物件負責管理資料持續性和多個共用的語意透過檢視此相同`DocData`。 如果`DocData`物件支援`IOleCommandTarget`介面，它將會包含在 UIShell 命令路由。  
  
 DocObject  
 用來裝載主機提供的範圍內的 UI 技術。 這個詞彙更具體來說，是指支援任何內嵌`IOleDocument`和相關的介面。 這項技術有許多潛在的應用程式，例如 COM 文件的實作詳細資料，在 Visual Basic 5.0 中的工具視窗時，Visual Basic 6.0 等 ActiveX 設計工具。  
  
 文件  
 用來參考以一般方式整個文件，同時`DocData`和`DocView`。 例如，包含 DocumentFrame `DocView`，但它也會保留的參考`DocData`處理持續性。  
  
 DocView  
 DocObject/內嵌/Windowpane> 與使用者互動檢視和管理基礎`DocData`。 請注意，使用者執行不會利用是一部分的文件/檢視區隔`DocObject`介面設計。 使用者用來做為檢視，而不要使用更抽象的 （和較正式） 的概念稱為基礎資料的整個 DocObject `DocData`。 `DocView` 物件永遠會內嵌在 IDE 的文件框架物件 （MDI 子視窗）。  
  
 DTE  
 `DTE` （開發工具擴充性） 的物件是 Visual Studio automation 模型，可讓您以程式設計的方式自動化和擴充 IDE 的最高的存取點。  
  
 動態說明 視窗  
 工具視窗由 IDE 所實作，並顯示一份查閱關鍵字或 F1 說明主題。  
  
 編輯器  
 實作的程式碼 （類別的 CLSID） `DocView`。 它也會實作`DocData`支援檢視/資料分離，則為。  
  
 擴充功能  
 此功能可修改、 自訂或加入 IDE。 您建立使用 automation 模型或 Vspackage 的延伸模組。  
  
 外部編輯器  
 編輯器不是專用 ide，例如 Microsoft Word。 它已註冊透過自己的機制，並可以使用此 IDE 外。 如果可以內嵌此編輯器中，會出現在 IDE 中視窗內。 如果無法內嵌，會建立個別的最上層視窗。  
  
 階層  
 樹狀結構的節點，每個節點相關聯的一組屬性。  
  
 獨立的最上層元件  
 元件會使用非強制回應的最上層視窗，也可以有效地運作為獨立的應用程式視窗，但會實作為同處理序物件。 因此，最上層的獨立元件必須協調模式和訊息迴圈服務和 IDE。 在處理程序物件沒有自己的訊息迴圈。  
  
 資訊提供者  
 資訊提供者是模組，可以查閱關鍵字，並傳回的表單中的主題，清單`IVsUserContextItem`物件。 若要提供 F1 和查閱關鍵字項目資訊提供者，註冊已編譯的說明檔 (。HxS) 與系統。 這些檔案中的說明主題用來提供動態說明 視窗中顯示和顯示使用者是否按下 F1 主題清單。  
  
 在就地元件  
 實作 VSPackage 物件`IOleInPlaceComponent`介面來管理以視覺化方式包含在由 IDE 所擁有的文件視窗的視窗。 在就地元件不會參與標準 OLE 功能表合併;改用他們將其使用者介面項目整合到 IDE。  
  
 有兩種類型的就地元件： 硬式編碼就地元件和控制項的元件。  
  
 硬式編碼就地元件有功能表、 工具列和已緊密整合到 IDE，並顯示為如果它們直接內建 IDE 的使用者介面的命令。  
  
 元件控制項不需要任何整合到 IDE; 自己使用者介面項目而是使用 IDE 的功能表、 命令和工具列。 比方說，粗體顯示的命令無法使用要以粗體顯示在表單中內嵌的 rtf 文字控制項內選取的字。 不過，元件控制項可以要求會顯示動態已安裝的特定元件的 UI 項目。  
  
 語言服務  
 一組物件，可讓 VSPackage 開發人員實作功能的電腦語言程式碼編輯器，例如文字將標記與上色功能。  
  
 其他檔案專案  
 用來存放不在任何專案中的開啟檔案的專案。 不會保存此專案中的項目清單。  
  
 專案  
 COM 物件所實作或專案所構成的階層物件`IVsHierarchy`介面。  
  
 特定專案設計工具或編輯器  
 此設計工具不能獨立專案類型。 特定專案的所有設計工具必須在登錄中輸入其編輯器 Factory 的資訊。 IDE 然後可以具現化設計工具時在特定專案中開啟特定檔案類型。  
  
 專案類型 視窗  
 視窗持續追蹤目前作用中的專案階層架構和項目，從全域範圍內容。 專案類型 windows 使用`SVsTrackSelectionEx`服務警示變更的 IDE，並向使用者顯示的意見反應。 方案總管 是 專案類型 視窗的範例。  
  
 屬性視窗  
 先前稱為屬性瀏覽器。  
  
 參考為基礎的專案  
 不需要是相同的目錄中專案的檔案的專案。 相反地，其他不相關的目錄中檔案的參考儲存和維護專案本身。  
  
 執行中的文件表格  
 內部結構，IDE 會維護所有目前開啟的文件的清單。 這份清單包括在記憶體，不論是否目前正在編輯的文件中的所有開啟的文件。 文件是儲存，包括預存程序，在編輯器中，專案中的檔案或主專案檔 （例如，*.vcproj 檔案） 中開啟任何項目。  
  
 選取項目內容  
 資料是在 IDE 中的每個視窗的詳細資料的一部分，用來追蹤作用中的選取項目。 選取項目內容所組成：  
  
-   指標`IVsHierarchy`專案階層架構的介面  
  
-   專案項目的項目識別項。  
  
-   指標`ISelectionContainer`介面提供存取作用中物件的屬性。  
  
-   項目值的陣列。  
  
 服務  
 一組位於單一的 COM 物件的 COM 介面的合約。 當您建立服務，這由 GUID 所識別，您會定義 COM 介面的集合都包含在內的服務。 COM 物件會使用服務來彼此通訊。  
  
 方案  
 與使用者的運作方式的相關專案的群組。  
  
 標準的設計工具  
 此設計工具可以使用獨立於專案類型。 所有標準的設計工具必須在登錄中輸入其編輯器 Factory 的資訊。 IDE 然後可以具現化設計工具只要開啟包含特定副檔名的檔案。 資料必須保存至檔案。  
  
 標準編輯器  
 可以使用獨立於任何特定專案類型的編輯器。 這類編輯器都有 EditorFactories 登錄中進行註冊。 這可讓 IDE 來找出並叫用編輯器。  
  
 標準 OS 編輯器  
 內嵌不是 Visual Studio 特定。 已註冊使用已知的 Win32 索引鍵 （例如 Win32 總管知道如何叫用）。 如果這類編輯器可以內嵌，編輯器仍然出現在其在 IDE 中的位置。 否則，會建立個別的最上層視窗，這類的編輯器。  
  
 子內容包  
 `IVsUserContext`物件連結到的內容封包。 此物件會保存查閱關鍵字、 F1 關鍵字和屬性的 IDE 元件中的選取範圍。 子內容的範例包括命令工具視窗或在編輯器中的關鍵字。  
  
 工作清單  
 工具視窗由 IDE 所實作，並顯示清單中的工作。  
  
 文字緩衝區  
 物件的一般名稱`VSTextBuffer`。  
  
 文字檢視  
 物件的一般名稱`VSTextView`。  
  
 工具的最上層元件  
 作業為非強制回應的快顯視窗，協調緊密地與 IDE 的使用者介面元件。 最上層的獨立元件，例如工具最上層元件也必須協調模式和訊息迴圈服務和 IDE。  
  
 最上層的元件  
 管理非強制回應的最上層視窗，而不是視窗工作區 IDE VSPackage 物件。 最上層元件實作`IOleComponent`介面，以充分利用存取的訊息迴圈服務為閒置的時間。  
  
 UI 作用中  
 為可見，且目前具有焦點的 VSPackage 物件。  
  
 UI 階層架構  
 COM 物件實作`IVsUIHierarchy`介面，讓階層的顯示。 實作 UI 階層視窗`ISelectionContainer`介面更新屬性視窗; 其他專案類型的視窗可以使用此實作中，如有需要。  
  
 VSCT  
 Visual Studio 命令表。 .Vsct 檔包含的位置和行為的功能表、 工具列和命令，以 XML 格式的相關資訊。  
  
 VSPackage  
 提供一或多個項目會擴充 Visual Studio IDE 的軟體可安裝部分： 使用者介面、 服務、 專案類型或編輯器/設計工具。 VSPackage 包含實作的 COM 物件`IVsPackage`介面以及一個或多個其他 COM 物件實作其他介面，以支援選取項目和其他功能。 此外，VSPackage 也有特定的註冊需求。