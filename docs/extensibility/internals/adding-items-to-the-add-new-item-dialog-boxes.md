---
title: 新增項目新增到「新增新項目」對話框 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710221"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>新增項目新增項目新增項目對話框
向「**添加新項目**」對話框添加項的過程從註冊表項開始。 若以下註冊表項目所示 **,「AddItemTemplates」** 部分包含目錄的路徑和名稱,其中放置了「**添加新項目」** 對話框中提供的項。

> [!NOTE]
> 代碼段緊接的表包含有關註冊表項的其他資訊。

 此部分位於**HKEY_LOCAL_MACHINE_SOFTWARE_微軟[VisualStudio]14.0Exp_專案**下。

 第一個 GUID 是此類專案的 CLSID;第二個 GUID 指示「新增項目」樣本的已註冊項目類型:

 **\\[C061DB26-5833-11D2-96F5-0000000000]\\新增項目\\樣本範本Dir\\[ACEF4EB2-57CF-11D2-96F4-000000000000000]\\1**

 **@**• #6

 **樣本Dir** = \\&gt;&lt;&lt;視覺化工作室 SDK 安裝路徑 VS 整合一些資料夾一些套件一些項目專案\\\\&lt;&gt;\\&lt;&gt;\\&lt;&gt;\\&gt;

 **排序優先權**= dword:00000064

| 名稱 | 類型 | 資料(來自 *.rgs*檔案) | 描述 |
|------------------|-----------| - | - |
| * (預設) | REG_SZ | ±%IDS_ADDITEM_TEMPLATES_ENTRY% | **添加項目**範本的資源 ID。 |
| 瓦爾範本Dir | REG_SZ | %TEMPLATE_PATH%\\&lt;某些項目項目&gt; | **"添加新專案**"嚮導的對話框中顯示的專案項的路徑。 |
| Val 排序優先權 | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]( ) | 確定「**新增新項目」** 對話框中顯示的檔案的樹節點中的排序順序。 |

> [!NOTE]
> Visual C# 和視覺化基本項目類型的 GUIDS 如下所示:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: [FAE04EC0-301F-11D3-BF4B-00C04F79EFBC]
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]:[F184B08F-C81C-45F6-A57F-5ABD9991F28F]

 **TemplatesDir**列出的目錄*\\&lt;(%TEMPLATE_PATH%&gt;某些項目專案*)是 **「新增新專案」** 對話框樹左側的節點。 樹中的其他元素基於該根目錄中的子目錄。 可添加到專案中的檔案是 **「新增新項目」** 對話框右側窗格中的項目。

 通常,此資料夾將包含專案的範本檔,如範本 HTML 或 *.cpp*檔,以及用於啟動精靈的任何 *.vsz*檔案。 要控制項目的顯示方式,還可以包括用於本地化目錄名稱和圖示的 *.vsdir*檔案。 當地語系化字串是顯示在「**新增新項目」** 對話方塊樹中表示此節點的對話框中顯示的標題。

 但是,您不必在一個 *.vsdir*檔中擁有所有內容。 對於目錄中的每個專案,可以有一個 *.vsdir*檔。 關於詳細資訊,請參閱精靈[(.vsz) 檔案與](../../extensibility/internals/wizard-dot-vsz-file.md)[樣本目錄標題 (.vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。

> [!NOTE]
> 樣本目錄中的 *.vsdir*檔是可選的。 如果只想將專案元素放在目錄中並在 **「添加新專案」** 對話框中顯示,則可以將該檔放在**樣本表**表中指定的範本目錄中。 然後,該檔將顯示在該專案的「**添加新專案」** 對話框的右側窗格中。 但是,如果要顯示檔的本地化標題或圖示,則必須在範本目錄中至少包含一個 *.vsdir*檔。

## <a name="group-project-items"></a>群組項目項目
 如果要在 **「添加新專案」** 對話方塊樹中的資料夾中包含樣本組,則必須在根範本目錄下具有包含其中項的子目錄。 向使用者顯示「**添加新項目**」對話框時,他們還會看到子資料夾,並能夠從這些資料夾中選擇專案元素。

 代碼段中的排序優先順序確定在樹中相對於樹節點的其他元素創建此範本目錄的位置。 對於「**添加新專案」** 對話框,排序優先順序是必須包含的,以便項目將顯示在對話框中的正確位置。

 您還可以實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>該介面來篩選「**添加新項目」** 對話框中顯示的內容。 通過實現此介面,可以在磁碟上設置一個範本目錄,其中包含 50 個樣本和嚮導檔。 這樣,您可以具有不同的項目類型,其中 20 個檔屬於一個項目類型,其他 30 個檔屬於另一個項目類型,所有檔都位於一般類型的專案中。 這樣,根據創建的專案範本,可以顯示一組不同的範本檔。

 例如,在可視化基本專案中,您可能具有 Web 專案和用戶端專案。 Web 表單是要加入客戶端專案的有用項,並且視窗窗體不是要添加到 Web 伺服器專案的有用項。 因此,您可以創建一個範本目錄,其中包含這兩種類型的專案的所有檔。 然後,通過實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>,可以隱藏不應根據專案中的專案或專案設置類型顯示的專案。

## <a name="filter-project-items"></a>篩選項目項目項目
 `IVsFilterAddProjectItemDlg2`提供以下欄方式篩選樹(左窗格)和專案檔(右窗格)中的元素:

- 由 提供的本地化名稱(顯示在 *.vsdir*檔案中的對話框中顯示的`IVsFilterAddProjectItemDlg`標題)。

- 按磁碟上的檔案與資料夾(非本地化 = 沒有 *.vsdir*檔案)提供`IVsFilterAddProjectItemDlg`的實際名稱。

- 按類別,由`IVsFilterAddProjectItemDlg2`提供。

  要按類別進行篩選,請向 *.vsdir*檔中的項(如 Visual Basic 中的*Web 窗體*或*用戶端項*)提供類別字串。 然後,對話框代碼從 *.vsdir*檔檢索類別分類並將其傳遞給您。 然後,您可以將該資訊傳遞給您的實現,`IVsFilterAddProjectItemDlg2`以按類別篩選「**新增新項目**」 對話框。 您還可以篩選網頁的專案或作為用戶端 Win32 應用程式案例。 此外,您可以將標記的項目[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]標識為 Microsoft 基礎類 (MFC) 或活動範本庫 (ATL) 項。 標識這些專案時,專案系統可以定義自己的分類,以便可以根據類別和分類篩選系統。

  如果實現此篩選器功能,則不必映射應隱藏的每個項的表。 只需將項分類為類型,並將分類放在 *.vsdir*檔或檔中即可。 然後,您可以通過實現介面來隱藏具有特定分類的任何項。 這樣,您可以根據專案中的狀態使"**添加新專案"** 對話方塊中的項保持動態。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [註冊項目和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [通常用於延伸項目的物件的 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [新增項目和項目項目樣本](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [樣本目錄描述 (.vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [匯入匯(.vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)
