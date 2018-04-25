---
title: 在 Visual Studio for Mac 中設定 Subversion 存放庫
description: 在 Visual Studio for Mac 中使用 Git 和 Subversion。
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: e6b6fd600d3f32c77651b9a4fbb0dff2cd754bcb
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="setting-up-a-subversion-repository"></a>設定 Subversion 存放庫

Subversion 是集中式版本控制系統。 這表示有單一伺服器包含所有檔案和修訂，而使用者可以從中簽出任何檔案的任何版本。 從遠端 Subversion 存放庫簽出檔案時，使用者將會收到存放庫在該時間點的快照集。

開始使用 Subversion 之前，必須安裝 Xcode 命令列工具，因為它們包含正確的 svn 套件。 您可以使用下列命令，檢查終端機中是否已安裝 SVN：

`svn h`

1. 線上建立免費 SVN 存放庫。 在此範例中，已使用 [Assembla](https://app.assembla.com/)。 建立之後，將會提供 URL，以用來連線至存放庫： 

    ![取得並複製 SVN URL](media/version-control-subversion1-sml.png)

2. 開啟或建立 Visual Studio for Mac 專案。

3. 以滑鼠右鍵按一下專案，然後選取 [版本控制] > [Publish in Version Control] (在版本控制中發行)： 

    ![開始發行專案](media/version-control-subversion2.png)

4. 在 [連線到存放庫] 索引標籤上，從頂端下拉式清單中選取 [Subversion]。

5. 輸入步驟 1 中的 URL。 根據預設，這應該填入其他欄位： 

    ![選取存放庫和輸入詳細資料對話方塊](media/version-control-subversion3.png)

7. 按一下 [確定]，然後按 [發行] 進行確認。

7. 系統可能會提示您輸入建立存放庫之網站的認證。 輸入這些資訊，如下所示：

    ![](media/version-control-subversion5.png)

8.  現在應該可以在版本控制功能表中看到所有可用的版本控制命令。

