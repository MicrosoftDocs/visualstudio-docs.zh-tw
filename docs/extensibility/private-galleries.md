---
title: 私人畫廊 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4056e4dedf06ffe86755bf946c77032d6f6782dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702045"
---
# <a name="private-galleries"></a>私人畫廊
以將控制項、樣本和工具發布到組織 Intranet 上的*專用函式庫*,可以共用這些控制項、樣本和工具,如下所示:

- 創建 Atom (RSS) 源,以連接到 Intranet 上配置適當的中央位置(儲存庫)。 有關詳細資訊,請參閱[如何:為專用庫創建 Atom 源](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)。

- 分發描述私有庫的 *.pkgdef*檔。 我們建議對希望同時將專用庫連接到多台計算機的管理員進行此配置。

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>將專用函式庫加入視覺化工作室中的擴充與更新
 當專用函式庫可用時,您可以將新增到 Visual Studio 中**延伸與更新**。

 ![[擴充管理員] 的 [新增] 對話方塊](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>新增專用函式庫加入到延伸

1. 在選單欄上,選擇 **「工具** > **選項**」。

2. 在 **"環境'** 節點中,選擇 **"擴展"和"更新**"。

3. 選擇 [加入]**** 按鈕。

4. 在 **「名稱」** 欄位中,輸入專用庫的名稱,`My Gallery`例如。

5. 在**URL**欄位中,輸入託管專用庫的 Atom 源或 SharePoint 網站的 URL。

    1. 如果主機是連線到專用函式庫的 Atom 源,則網址將http://www.mywebsite/mygallery/atom.xml類似於此網址: 。  此網址可以引用檔案或網路路徑。

    2. 如果主機是 SharePoint 站點,則網址將http://mysharepoint/sites/mygallery/forms/AllItems.aspx類似於此 網站: 。

### <a name="manage-private-galleries"></a>管理私人畫廊
 管理員可以通過修改每台電腦上的系統註冊表,同時使專用庫可供多台電腦使用。 為此,請創建一個 *.pkgdef*檔,描述新的註冊表項及其值。  此檔的格式如下。

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 有關詳細資訊,請參閱[操作方式:使用註冊表設置管理專用庫](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)。

## <a name="install-extensions-from-a-private-gallery"></a>從專用函式庫安裝擴充
 您可以在**擴充和更新**中從專用庫搜索和安裝 Visual Studio 擴充。 以下步驟使用名為`My Gallery`的 私有庫。

 ![安裝私人組件庫的 [擴充管理員]](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>從專用函式庫搜尋並安裝擴充

1. 在選單列上,選擇 **「工具** > **擴展」和「更新**」。

2. 在左側窗格中,選擇 **「連線擴展**」,然後選擇 **「我的庫**」。

3. 在右邊窗格中,選擇副檔名,然後選擇「**下載**」按鈕。

## <a name="update-extensions-from-a-private-gallery"></a>從專用函式庫更新延伸
 當 Visual Studio 擴充的新版本發布到專用庫中時,您可以更新已安裝的擴展。 以下步驟使用名為`My Repository`的 私有庫。

 ![[擴充管理員] 更新私人組件庫](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>從專用函式庫更新已安裝的延伸

1. 在選單列上,選擇 **「工具** > **擴展」和「更新**」。

2. 在左側窗格中,選擇 **「更新**」,然後選擇 **「我的存儲庫**」 。。

3. 在右邊窗格中,選擇副檔名,然後選擇 **「更新**」按鈕。

## <a name="see-also"></a>另請參閱
- [尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)
- [船舶視覺工作室擴展](../extensibility/shipping-visual-studio-extensions.md)
