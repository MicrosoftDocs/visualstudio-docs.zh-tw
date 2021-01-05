---
title: 設定 Subversion 存放庫
description: 瞭解如何在 Visual Studio for Mac 中將 Subversion 安裝和設定為集中式版本控制系統。
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.topic: how-to
ms.openlocfilehash: b5230958fa1624acf7609d6cad7d885e43c013d0
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847076"
---
# <a name="set-up-a-subversion-repository"></a>設定 Subversion 存放庫

Subversion 是集中式的版本控制系統，這表示會有包含所有檔案和修訂的單一伺服器，而使用者可以從中簽出任何檔案的任何版本。 從遠端 Subversion 存放庫簽出檔案時，使用者會收到存放庫在該時間點的快照集。

若要為您的版本控制使用 Subversion，您必須先將其安裝至電腦。 若要確認您的電腦是否已安裝 Subversion，請在終端機中使用以下命令：

```bash
svn --version
```

此命令會傳回版本號碼。

如果尚未安裝 Subversion，安裝 _Xcode Command Line Tools_ 是取得它最輕鬆的方法。 使用下方命令即可安裝 Xcode Command Line Tools 與 Subversion。

```bash
xcode-select --install
```

Subversion 安裝至電腦後，請使用下列步驟在 SVN 中發佈您的專案。

1. 線上建立免費 SVN 存放庫。 在此範例中，已使用 [Assembla](https://app.assembla.com/)。 建立之後，將會提供 URL，以用來連線至存放庫：

    ![複製 SVN URL](media/version-control-subversion1-sml.png)

2. 開啟或建立 Visual Studio for Mac 專案。

3. 以滑鼠右鍵按一下專案，然後選取 [版本控制] > [Publish in Version Control] (在版本控制中發行)：

    ![開始發行專案](media/version-control-subversion2.png)

4. 在 [連線至存放庫] 索引標籤中，從頂端的下拉式清單選取 [Subversion]。

5. 輸入步驟 1 中的 URL。 輸入 URL 後，預設會填入其他欄位：

    ![選取存放庫和輸入詳細資料對話方塊](media/version-control-subversion3.png)

7. 按一下 [確定]，然後按 [發行] 進行確認。

7. 若出現提示，請輸入建立存放庫之網站的認證，如下所示：

    ![輸入 Subversion 存放庫的認證](media/version-control-subversion5.png)

8. 現在應該可以在版本控制功能表中看到所有可用的版本控制命令。

## <a name="see-also"></a>請參閱

- [使用 Subversion](working-with-subversion.md)