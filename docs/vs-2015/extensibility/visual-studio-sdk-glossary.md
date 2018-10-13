---
title: Visual Studio SDK 字彙表 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20310605ed73247958287903a8eb3926ee55ba1d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225546"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK 字彙表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

這份字彙表提供所用的詞彙定義[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]文件。  
  
## <a name="terms"></a>詞彙  
 Add-In - 增益集  
 公用程式應用程式、 驅動程式或加入至主應用程式的其他軟體。 在 Visual Studio 整合式的開發環境 (IDE) 中，增益集是自動化架構的應用程式擴充功能的 IDE。  
  
 Automation 模型  
 Automation 模型中，已知在舊版的 Visual Studio 擴充性模型是程式設計介面，可讓您存取的基礎常式該磁碟機的 IDE。 增益集、 精靈和巨集使用 automation 模型來控制中的物件或擴充 IDE 功能。  
  
 命令 UI 內容  
 使用 UI 命令或工具列等項目的可見性 GUID 的關聯。 命令 UI 內容會與選取範圍內容不同，因為它不會附加到視窗。  
  
 命令 UI 內容可以用來：  
  
-   將出現時啟動特定視窗的工具列中的 GUID。  
  
-   指派給命令的可用性的 GUID，而不需要載入或執行 VSPackage。  
  
-   指派會影響使用中的索引鍵繫結的 GUID。  
  
-   指派即可錄製巨集的 GUID。  
  
-   指派的 GUID，可啟用偵錯模式，或設計] 和 [在編輯器中的執行的模式之間切換。  
  
 元件  
 透過應用程式的功能部分不需要有預先存在的任何資訊的軟體實作該應用程式的軟體的部分。 應用程式和元件之間的通訊是只會透過 OLE 樣式介面。  
  
 元件管理員  
 服務， `SOleComponentManager`，它會提供最上層元件的非使用者介面協調服務。 `SOleComponentManager`服務會實作`IOleComponentManager`介面。  
  
 元件 UI 管理員  
 服務， `SOleComponentUIManager`，它會提供使用者介面協調服務。 `SOleComponentUIManager`服務會實作`IOleComponentUIManager`和`IOleInPlaceComponentUIManager`介面。  
  
 內容包  
 `IVsUserContext`物件 （COM 物件） 附加至環境元件。 此物件會保存查詢關鍵字、 F1 關鍵字和相關元件的屬性。 內容包此外會指向連結到其任何子內容包。  
  
 內容提供者  
 在 IDE 具有與其相關聯的內容封包的元件。 這類元件包括工具視窗、 編輯器或專案階層架構。  
  
 設計工具  
 程式設計介面，可讓使用者管理 UI （表單、 按鈕和其他控制項） 的項目。  
  
 DocData  
 COM 物件，封裝的世界中的文件的基礎資料沒有文件/檢視表隔離 （例如，在文字編輯器案例中，這會是所有的文字編輯器檢視文字緩衝區）。 如果 EditorFactory 未提供此物件時，IDE 會製造代替它的其中一個。 此物件負責管理資料持續性及多個共用的語意透過檢視此相同`DocData`。 如果`DocData`物件支援`IOleCommandTarget`介面，它將會包含在 UIShell 命令路由。  
  
 DocObject  
 用來裝載主機提供的範圍內的 UI 技術。 更具體來說，這個詞彙是指支援任何內嵌`IOleDocument`和相關的介面。 這項技術有許多潛在的應用程式，例如 COM 文件的實作詳細資料，在 Visual Basic 5.0 中的工具視窗時，ActiveX 設計工具，在 Visual Basic 6.0 中，依此類推。  
  
 文件  
 用來以一般方式參考文件的整體 — 同時`DocData`而`DocView`。 比方說，DocumentFrame 包含`DocView`，但它也會保留參考`DocData`處理持續性。  
  
 DocView  
 DocObject/內嵌/視窗窗格與使用者互動來檢視和管理基礎`DocData`。 請注意，使用者不會是一部分的文件/檢視分離的利用`DocObject`介面設計。 使用者用來做為檢視，而不是使用所謂的基礎資料的抽象 （和較不正式） 概念的整個 DocObject `DocData`。 `DocView` 物件永遠會內嵌在 IDE 的文件框架物件 （的 MDI 子視窗）。  
  
 DTE  
 `DTE` （開發工具擴充性） 的物件是在 Visual Studio automation 模型，可讓您以程式設計的方式自動化及擴充 IDE 的最上層的存取點。  
  
 動態說明 視窗  
 工具視窗，由 IDE 所實作，並顯示一份查閱關鍵字或 F1 說明主題。  
  
 編輯器  
 實作的程式碼 （類別，CLSID） `DocView`。 它也會實作`DocData`是否支援檢視/資料區隔。  
  
 擴充功能  
 修改、 自訂，或加入 IDE 的功能。 您建立使用 automation 模型的 Vspackage 擴充功能。  
  
 外部編輯器  
 編輯器不是專用的 ide，例如 Microsoft Word。 它已註冊透過自己的機制，並可以在 IDE 外部使用。 如果此編輯器可內嵌，出現在 IDE 中的視窗內。 如果無法內嵌，則會建立個別的最上層視窗。  
  
 階層  
 節點樹狀結構，一組屬性相關聯的每個節點。  
  
 獨立的最上層元件  
 元件會使用非強制回應的最上層視窗，也能有效地作為獨立應用程式 視窗中，但會實作為同處理序物件。 因此，為獨立的最上層元件必須協調強制回應性和與 IDE 的訊息迴圈服務。 在處理程序物件並沒有自己的訊息迴圈。  
  
 資訊提供者  
 資訊提供者是可以查閱關鍵字並傳回的表單中的主題，清單的模組`IVsUserContextItem`物件。 若要提供 F1 和查閱關鍵字項目資訊提供者，註冊已編譯的說明檔 (。HxS) 與系統。 這些檔案中的 說明 主題可提供的動態說明 視窗中顯示和顯示使用者是否按下 F1 的主題清單。  
  
 就地元件  
 實作 VSPackage 物件`IOleInPlaceComponent`介面來管理以視覺化方式包含在由 IDE 所擁有的文件視窗的視窗。 就地元件不會參與標準 OLE 功能表合併;而是他們將其使用者介面項目整合到 IDE。  
  
 有兩種類型的就地元件： 硬式編碼在就地元件和元件的控制項。  
  
 硬式編碼在就地元件會有功能表、 工具列和已緊密整合到 IDE 中，顯示為如果它們已直接內建 IDE 使用者介面的命令。  
  
 元件的控制項不需要任何整合到 IDE; 其本身使用者介面項目而是它們使用 IDE 的功能表、 命令和工具列。 比方說，可以使用粗體的命令，要以粗體顯示在表單中內嵌的 rtf 文字控制項內選取的字。 不過，可以要求元件控制項，以動態方式安裝的元件特定 UI 項目會顯示。  
  
 語言服務  
 一組物件，可讓 VSPackage 開發人員實作功能的電腦語言程式碼編輯器，例如文字標記與上色功能。  
  
 其他檔案專案  
 用來館開啟的檔案不在任何專案中的專案。 在此專案中的項目清單不會保存。  
  
 專案  
 專案組成的階層物件或 COM 物件實作`IVsHierarchy`介面。  
  
 特定專案設計工具或編輯器  
 此設計工具不能獨立於專案類型。 所有的專案特定設計工具必須在登錄中輸入他們編輯器 Factory 的資訊。 IDE 然後可以具現化設計工具只要在特定專案中開啟特定檔案類型。  
  
 專案類型 視窗  
 會持續追蹤目前作用中的專案階層架構和項目從全域範圍內容視窗。 使用 專案類型 windows`SVsTrackSelectionEx`服務警示變更的 IDE，並向使用者顯示意見反應。 方案總管 是 專案類型 視窗的範例。  
  
 屬性視窗  
 先前稱為屬性瀏覽器。  
  
 參考為基礎的專案  
 不需要為相同的目錄中專案的檔案的專案。 相反地，其他不相關的目錄中檔案的參考儲存和維護專案本身。  
  
 執行文件資料表  
 內部結構的 IDE 會維護所有目前開啟的文件的清單。 這份清單會納入記憶體，不論是否目前正在編輯的文件中的所有開啟的文件。 文件是儲存，包括開啟編輯器，在專案中的檔案或主要專案檔 （例如，*.vcproj 檔案） 中的預存程序的任何項目。  
  
 選取項目內容  
 資料是在 IDE 中的每個視窗的詳細資料的一部分，用來追蹤使用中的選取項目。 選取範圍內容所組成：  
  
-   指標`IVsHierarchy`專案階層架構的介面  
  
-   專案項目的項目識別項。  
  
-   指標`ISelectionContainer`提供存取的作用中的物件屬性的介面。  
  
-   項目值的陣列。  
  
 服務  
 一組 COM 介面，可位於單一的 COM 物件的合約。 當您建立的服務，可由 GUID 識別，您會定義執行服務的 COM 介面組。 COM 物件會使用服務來彼此進行通訊。  
  
 解決方案  
 與使用者的運作方式的相關專案的群組。  
  
 標準的設計工具  
 一種設計工具，可以使用獨立的專案類型。 所有標準的設計工具必須在登錄中輸入其編輯器 Factory 的資訊。 IDE 然後可以具現化設計工具只要開啟具有特定副檔名的檔案。 資料必須保留在檔案中。  
  
 標準編輯器  
 可以使用獨立於任何特定專案類型的編輯器。 這類編輯器有 EditorFactories 在登錄中。 這可讓 IDE 找出並叫用編輯器。  
  
 標準的 OS 編輯器  
 內嵌不是 Visual Studio 特定。 已註冊使用已知的 Win32 索引鍵 （例如，Win32 檔案總管知道如何叫用）。 如果可以內嵌這類編輯器，編輯器仍出現在其在 IDE 中的位置。 否則，另一個最上層視窗會建立這類的編輯器。  
  
 子內容包  
 `IVsUserContext`物件連結到內容包。 此物件會保存查詢關鍵字、 F1 關鍵字和選取範圍內的 IDE 元件的屬性。 子內容的範例包含命令，在 [工具] 視窗中或在編輯器中的關鍵字。  
  
 工作清單  
 工具視窗由 IDE 所實作，會顯示一份作用中工作。  
  
 文字緩衝區  
 物件的一般名稱`VSTextBuffer`。  
  
 文字檢視  
 物件的一般名稱`VSTextView`。  
  
 工具的最上層元件  
 表示非強制回應快顯視窗中，協調緊密地與 IDE 的使用者介面元件。 最上層的獨立元件，例如強制回應性和與 IDE 的訊息迴圈服務，也必須協調工具最上層的元件。  
  
 最上層的元件  
 管理非強制回應的最上層視窗，而不是 IDE 視窗工作區 VSPackage 物件。 最上層的元件會實作`IOleComponent`介面，以利用訊息迴圈服務，例如存取到閒置的時間。  
  
 作用中的 UI  
 會顯示，且目前具有焦點的 VSPackage 物件。  
  
 UI 階層架構  
 COM 物件實作`IVsUIHierarchy`以階層顯示的介面。 實作 UI 階層視窗`ISelectionContainer`介面來更新 [屬性] 視窗; 其他專案類型 windows 才能使用此實作中，如有需要。  
  
 VSCT  
 Visual Studio 命令資料表。 .Vsct 檔包含資訊的位置和行為的功能表、 工具列和 XML 格式的命令。  
  
 VSPackage  
 提供一或多個項目會擴充 Visual Studio IDE 的軟體可安裝部分： 使用者介面、 服務、 專案類型或編輯器/設計工具。 VSPackage 所組成的 COM 物件，實作`IVsPackage`介面和一個或多個其他 COM 物件實作其他介面，以支援選取項目和其他功能。 此外，VSPackage 都有特定的註冊需求。

