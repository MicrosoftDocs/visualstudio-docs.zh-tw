---
title: 安裝本機說明文件
description: 使用 Microsoft Help Viewer 來安裝和管理本機說明文件。 新增、移除、更新和移動安裝在您電腦上的說明內容。
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer]
- updating local content [Help Viewer]
- Help Viewer, content installation source
- Help Viewer, updating local content
- Help Viewer, changing content installation source
- installing local content [Help Viewer]
- content installation source [Help Viewer]
- downloading content [Help Viewer]
- removing local content [Help Viewer]
- Help Viewer, removing local content
- Help Viewer, installing local content
- Help Viewer, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 14091ecd5adc76762901c02c582c845aa0dbd513
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944117"
---
# <a name="install-and-manage-local-content"></a>安裝與管理本機內容

藉由使用 Microsoft Help Viewer，您可以加入、移除、更新和移動安裝於您電腦上的說明內容，以符合您的軟體開發需求。

若要管理本機電腦上的內容，您必須以具有系統管理員權限的帳戶登入。 此外，如果您在企業環境中使用，可能會無法管理本機內容，因為系統管理員可能會為您的組織做決策。 如需詳細資訊，請參閱說明 [檢視器系統管理員指南](../help-viewer/administrator-guide.md)。

## <a name="change-the-content-installation-source"></a>變更內容安裝來源

根據預設，說明檢視器會使用 Microsoft 線上服務作為來源來安裝內容。 通常您不應變更內容的來源，除非您在企業環境上使用，為此系統管理員早已安裝內容在另一個位置。

### <a name="to-change-the-content-installation-source"></a>變更內容安裝來源

1. 在 [管理內容] 索引標籤上，選擇 [磁碟] 選項按鈕。

    > [!NOTE]
    > 如果系統管理員阻止您修改內容安裝來源，則 [磁碟] 選項無法使用。 如需詳細資訊，請參閱說明 [檢視器系統管理員指南](../help-viewer/administrator-guide.md)。

2. 請執行下列其中一個步驟：

    - 輸入 *.msha* 檔案的路徑或服務端點的 URL。

    - 選擇 [流覽 (**...**) ] 按鈕流覽至 *.msha* 檔案。

    - 在清單中，選擇最近使用的項目。

## <a name="download-and-install-content-locally"></a>在本機下載及安裝內容

如果您在本機電腦上下載及安裝內容，就可以在沒有網際網路連線時檢視主題。

> [!IMPORTANT]
> 若要安裝內容，您必須以具有系統管理權限的帳戶登入。

> [!NOTE]
> 如果 Visual Studio IDE 設定為英文以外的語言，您可以安裝英文內容、當地語系化內容或兩者兼具。 不過，如果您只安裝英文版，且清除 [檢視器選項] 對話方塊中的 [將英文內容包含在所有瀏覽索引標籤和 F1 要求中] 核取方塊，則不會出現任何內容。

### <a name="to-download-and-install-content"></a>下載及安裝內容

1. 選擇 [管理內容] 索引標籤。

2. 在內容清單中，選擇 [新增] 連結，這位於您想要下載並安裝的書籍旁邊。

     本書已加入 [暫止的變更] 清單，您所指定書籍的預估大小會出現在該清單下方。 由於有些書籍會共用主題，所以多本書籍的總下載大小可能小於每本指定書籍大小加在一起的結果。

3. 選擇 [更新] 按鈕。

     您所指定的書籍會隨任何您早已安裝在電腦上的書籍更新一併安裝。 安裝時間不盡相同，但是您可以在狀態列中檢視進度。

## <a name="remove-local-content"></a>移除本機內容

您可以從電腦移除不要的內容，以節省磁碟空間。

> [!IMPORTANT]
> 您必須擁有系統管理權限才能移除內容。

> [!NOTE]
> 如果 Visual Studio IDE 設定為英文以外的語言，而您又移除當地語系化內容和清除 [檢視器選項] 對話方塊中的 [將英文內容包含在所有瀏覽索引標籤和 F1 要求中] 核取方塊，則不會出現任何內容。

### <a name="to-remove-content"></a>移除內容

1. 選擇 [管理內容] 索引標籤。

2. 在內容清單中，選擇 [移除] 連結，此位於您想要移除的書籍旁邊。

     本書已新增 [暫止的變更] 清單。

3. 選擇 [更新] 按鈕。

     您所指定的書籍會從電腦移除。

## <a name="update-local-content"></a>更新本機內容

狀態列會指出您所安裝內容的更新何時可用。

> [!IMPORTANT]
> 如果您想要 **讓說明檢視器** 自動檢查線上更新，則必須開啟 [ **檢視器選項** ] 對話方塊，然後選取 [ **上線以檢查內容更新** ] 核取方塊。

### <a name="to-update-local-content"></a>更新本機內容

- 在狀態列右下角，選擇 [按一下這裡立即下載] 連結。

更新時間不盡相同，但是您可以在狀態列中檢視更新進度。

## <a name="move-local-content"></a>移動本機內容

您可以從本機電腦移動已安裝的內容到網路共用或本機電腦上的另一個分割，以節省磁碟空間。

> [!IMPORTANT]
> 若要移動內容，您必須以具有系統管理權限的帳戶登入。

### <a name="to-move-local-content"></a>移動本機內容

1. 在 [管理內容] 索引標籤上，選擇 [本機存放區路徑] 底下的 [移動] 按鈕。

     [移動內容] 對話方塊隨即開啟。

2. 在 [至] 文字方塊中，輸入一個不同的內容位置，然後選擇 [確定] 按鈕。

3. 當內容經移動後，請選擇 [關閉] 按鈕。

## <a name="see-also"></a>另請參閱

- [Microsoft Help Viewer](../help-viewer/overview.md)