---
title: 私用資源庫 |Microsoft Docs
description: 瞭解如何將您在 Visual Studio SDK 中開發的控制項、範本和工具張貼至私用資源庫，以共用這些控制項、範本和工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c64c5880fcdb1d6a1fb3d6fc7c71f55abf7cbbc1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069032"
---
# <a name="private-galleries"></a>私用資源庫
您可以藉由將控制項、範本和工具張貼到組織內部網路上的私用資源 *庫* ，來共用您所開發的控制項、範本和工具，如下所示：

- 建立 Atom (RSS) 摘要至您內部網路上 (存放庫) 適當設定的中央位置。 如需詳細資訊，請參閱 [如何：建立私用資源庫的 Atom](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)摘要。

- 散發描述私用資源庫的 *.pkgdef* 檔案。 如果系統管理員想要同時將私人資源庫連線到多部電腦，建議使用此設定。

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>在 Visual Studio 中將私人資源庫新增至擴充功能和更新
 當私人資源庫可供使用時，您可以將它新增至 Visual Studio 中的 **擴充功能和更新** 。

 ![[擴充管理員] 的 [新增] 對話方塊](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>將私用資源庫新增至擴充功能和更新

1. 在功能表列上，選擇 [**工具**  >  **選項**]。

2. 在 [ **環境** ] 節點中，選取 [ **擴充功能和更新**]。

3. 選擇 [新增] 按鈕。

4. 在 [ **名稱** ] 欄位中，輸入私用資源庫的名稱，例如 `My Gallery` 。

5. 在 [ **URL** ] 欄位中，輸入裝載私用資源庫之 Atom 摘要或 SharePoint 網站的 url。

    1. 如果主機是連接至私用資源庫的 Atom 摘要，則 URL 會類似下列內容： `http://www.mywebsite/mygallery/atom.xml` 。  這個 URL 可以參考檔案或網路路徑。

    2. 如果主機是 SharePoint 網站，則 URL 會類似下列內容： `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` 。

### <a name="manage-private-galleries"></a>管理私用資源庫
 系統管理員可以藉由在每部電腦上修改系統登錄，讓多部電腦都能使用私用資源庫。 若要完成此動作，請建立 *.pkgdef* 檔案，以描述新的登錄機碼及其值。  此檔案的格式如下所示。

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 如需詳細資訊，請參閱 [如何：使用登錄設定管理私用圖庫](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)。

## <a name="install-extensions-from-a-private-gallery"></a>從私用資源庫安裝擴充功能
 您可以在 [ **擴充功能和更新**] 中，從私用庫搜尋並安裝 Visual Studio 延伸模組。 下列步驟會使用名為的私用資源庫 `My Gallery` 。

 ![安裝私人組件庫的 [擴充管理員]](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>從私用元件庫搜尋及安裝延伸模組

1. 在功能表列上，選擇 [**工具**  >  **擴充功能和更新**]。

2. 在左窗格中，選取 [ **線上擴充** 功能]，然後選取 [我的資源 **庫**]。

3. 選取右窗格中的延伸模組，然後選擇 [ **下載** ] 按鈕。

## <a name="update-extensions-from-a-private-gallery"></a>更新私人資源庫中的延伸模組
 當私人資源庫中張貼新版本的 Visual Studio 延伸模組時，您可以更新已安裝的擴充功能。 下列步驟會使用名為的私用資源庫 `My Repository` 。

 ![[擴充管理員] 更新私人組件庫](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>從私用資源庫更新已安裝的擴充功能

1. 在功能表列上，選擇 [**工具**  >  **擴充功能和更新**]。

2. 在左窗格中，選取 [ **更新**]，然後選取 [我的存放 **庫**]。

3. 選取右窗格中的擴充功能，然後選擇 [ **更新** ] 按鈕。

## <a name="see-also"></a>另請參閱
- [尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)
- [寄送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)
