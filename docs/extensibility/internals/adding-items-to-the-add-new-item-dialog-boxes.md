---
title: 將專案加入至 [加入新專案] 對話方塊 |Microsoft Docs
description: 瞭解如何將專案加入至 Visual Studio 中的 [加入新專案] 對話方塊，讓您可以顯示要用於專案中的範本和專案專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 574cc5384018d14fdc05a834876002bbcbdbaaf7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079094"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>在 [加入新專案] 對話方塊中加入專案
在 [ **加入新專案** ] 對話方塊中加入專案的程式會以登錄機碼開頭。 如下列登錄專案所示，[ **AddItemTemplates** ] 區段包含可在 [ **加入新專案** ] 對話方塊中使用之專案的目錄路徑和名稱。

> [!NOTE]
> 緊接在程式碼區段後面的資料表包含有關登錄專案的其他資訊。

 本節位於 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects** 下。

 第一個 GUID 是此類型之專案的 CLSID;第二個 GUID 表示已註冊的 [新增專案] 範本專案類型：

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\AddItemTemplates \\ TemplatesDir \\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \\ 1**

 **@** = #6

   =  \\ TemplatesDir &lt;Visual Studio SDK 安裝路徑 &gt; \\ VSIntegration \\ &lt; SomeFolder &gt; \\ &lt; SomePackage &gt; \\ &lt; SomeProject &gt; \\ &lt; SomeProjectItems&gt;

 **SortPriority** = dword：00000064

| 名稱 | 類型 | 從 *.rgs* 檔案 (的資料)  | Description |
|------------------|-----------| - | - |
| @ (預設)  | REG_SZ | % IDS_ADDITEM_TEMPLATES_ENTRY% | **新增專案** 範本的資源識別碼。 |
| Val TemplatesDir | REG_SZ | % TEMPLATE_PATH% \\ &lt; SomeProjectItems&gt; | 在 [ **加入新專案** ] 嚮導的對話方塊中顯示之專案專案的路徑。 |
| Val SortPriority | REG_DWORD | 100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])  | 決定在 [ **加入新專案** ] 對話方塊中顯示之檔案的樹狀節點中的排序次序。 |

> [!NOTE]
> Visual c # 和 Visual Basic 專案類型的 GUID 如下所示：
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 針對 **TemplatesDir** 列出的目錄（ *% TEMPLATE_PATH% \\ &lt; SomeProjectItems &gt;*）是 [**加入新專案**] 對話方塊樹狀目錄左側的節點。 樹狀結構中的其他元素是以該根目錄內的子目錄為基礎。 可新增至專案的檔案是 [ **加入新專案** ] 對話方塊右窗格中的專案。

 此資料夾通常會包含您專案的範本檔案，例如範本 HTML 或 *.cpp* 檔案，以及用來啟動嚮導的任何 *.vsz* 檔。 若要控制專案的顯示方式，您也可以包含用來當地語系化目錄名稱和圖示的 *vsdir 檔案。* 當地語系化的字串是顯示在 [ **加入新專案** ] 對話方塊樹狀結構中，代表這個節點之對話方塊中的標題。

 不過，您不需要在同一個 *vsdir* 檔案中包含所有專案。 目錄中的每個專案都可以有一個 *vsdir 檔案。* 如需詳細資訊，請參閱 [Wizard ( .vsz) ](../../extensibility/internals/wizard-dot-vsz-file.md) 檔案和 [範本目錄描述 ( 的 vsdir) ](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)檔。

> [!NOTE]
> 範本目錄中的 *vsdir* 檔案是選擇性的。 如果您只想要在目錄中放入專案專案，並將它顯示在 [ **加入新專案** ] 對話方塊中，您可以將該檔案放在 **TemplatesDir** 語句中指定的 [templates] 目錄中。 檔案就會顯示在該專案的 [ **加入新專案** ] 對話方塊的右窗格中。 但是，如果您想要顯示檔案或圖示的當地語系化標題，您必須在 [範本] 目錄中包含至少一個 *vsdir 檔案。*

## <a name="group-project-items"></a>群組專案專案
 如果您想要在 [ **加入新專案** ] 對話方塊樹狀結構的資料夾中包含範本群組，您必須在根範本目錄下包含子目錄，以及其中的專案。 當使用者顯示 [ **加入新專案** ] 對話方塊時，他們也會看到子資料夾，而且可以選取專案中的專案專案。

 程式碼區段中的排序優先權會決定這個範本目錄在樹狀結構中建立的位置，相對於樹狀節點的其他元素。 在 [ **加入新專案** ] 對話方塊中，排序優先順序是您必須包含的所有專案，如此您的專案就會顯示在對話方塊中的正確位置。

 您也可以執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 介面，以篩選 [ **加入新專案** ] 對話方塊中顯示的內容。 藉由執行這個介面，您可以在包含50範本和 wizard 檔案的磁片上設定一個範本目錄。 如此一來，您可以有不同的專案類型，其中包含20個屬於一個專案類型的檔案、另一個屬於另一個專案類型的30個檔案，以及一般類型專案中可用的所有檔案。 透過這種方式，您可以根據所建立的專案範本，顯示一組不同的範本檔案。

 例如，在 Visual Basic 專案中，您可能會有 Web 專案和用戶端專案。 Web form 不是要加入至用戶端專案的實用專案，而且 windows forms 不是要加入至 Web 服務器專案的實用專案。 因此，您可以建立一個範本目錄，其中包含這兩種專案類型的所有檔案。 然後， <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 您可以根據專案中的專案或專案設定類型，隱藏不應顯示的專案。

## <a name="filter-project-items"></a>篩選項目專案
 `IVsFilterAddProjectItemDlg2` 提供篩選樹狀結構中的專案 (左窗格) 和專案檔 (右窗格中，以下列方式) ：

- By the localized names (captions displayed in the dialog box that is contained in the *.vsdir* file) provided by `IVsFilterAddProjectItemDlg`.

- 依磁片上的檔案和資料夾的實際名稱 (非當地語系化的，) 提供的任何 *vsdir* `IVsFilterAddProjectItemDlg` 檔案。

- 依類別（由提供） `IVsFilterAddProjectItemDlg2` 。

  若要依分類篩選，請在 [Visual Basic 中的 *Web 表單* 或 *用戶端專案* 中，提供類別字串給該類型的專案 *。* 對話方塊程式碼接著會從 *vsdir* 檔案中取出類別分類，並將其傳遞給您。 然後，您可以將該資訊傳遞至的執行， `IVsFilterAddProjectItemDlg2` 以依類別篩選 [ **加入新專案** ] 對話方塊。 您也可以篩選網頁或用戶端 Win32 應用程式案例的專案。 此外，您可以將 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 標記的專案識別為 Microsoft Foundation 類別 (MFC) 或 active template library (ATL) 專案。 當您識別這些專案時，專案系統可以定義自己的分類，以便根據類別和分類來篩選系統。

  如果您執行此篩選功能，就不需要對應每個應該隱藏之專案的資料表。 您可以直接將專案分類為類型，並將分類放入檔案 *中。* 然後，您可以藉由執行介面，隱藏任何具有特定分類的專案。 如此一來，您就可以根據專案內的狀態，讓 [ **加入新專案** ] 對話方塊中的專案變成動態。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [通常用來擴充專案的物件 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [新增專案與專案專案範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [範本目錄描述 ( 的 vsdir) 檔](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Wizard ( .vsz) 檔](../../extensibility/internals/wizard-dot-vsz-file.md)
