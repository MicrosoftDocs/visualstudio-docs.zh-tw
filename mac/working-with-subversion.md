---
title: 使用 Subversion
description: 瞭解如何在 Visual Studio for Mac 中使用 Subversion 作為集中式版本控制系統。
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: 512432a7210999e1d432494ec67bb2bf7a0e6a11
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846854"
---
# <a name="working-with-subversion"></a>使用 Subversion

Subversion 是集中式版本控制系統，可讓您簽出集中式資料的單一主要複本。 與 Git 相較之下，簽出 Subversion 存放庫不會複製整個存放庫，而只會取得該時間點的快照集。

Subversion 使用「複製-修改-合併」模型，允許使用者同時處理相同的存放庫。 這表示每位使用者都會建立集中式資料的本機或工作複本，接著就可以獨立處理它們。 會以時間形式合併使用者對工作複本的變更。

例如，假設使用者 A 和使用者 B 都從遠端存放庫簽出複本，而且他們都會修改檔案。 使用者 A 完成修改，並遠端進行認可。 使用者 B 在認可其工作之前，必須將遠端中的變更更新至其工作複本，進而與使用者 A 的變更合併。

下列各節中將探討如何在 Visual Studio for Mac 中使用 Subversion 進行版本控制。

下圖說明 Visual Studio for Mac 透過 [版本控制] 功能表項目所提供的選項：

![版本控制功能表項目](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>簽出...

開始使用遠端 Subversion 存放庫之前，請簽出存放庫，以在本機電腦上建立該目錄的工作複本。

若要了解如何在 Visual Studio for Mac 中使用 [簽出] 功能，請遵循[設定 Subversion 存放庫](set-up-subversion-repository.md)一節中的步驟。

## <a name="update-solution"></a>更新方案

使用遠端存放庫時，請務必記住，其他使用者可能正在修改檔案，進而導致您的工作複本過期。 為了處理這項預期的衝突，我們建議在開始工作及認可之前，一律先將任何變更從存放庫提取到您的方案。 若要執行提取變更，請選取 [版本控制] > [更新方案] 功能表項目。

## <a name="review-solution-and-commit"></a>Review Solution and Commit (檢閱方案並認可)

若要檢閱檔案中的變更，請使用每個文件上的 [變更]、[改動者]、[記錄] 和 [合併] 索引標籤，如下圖中所示：

![版本控制索引標籤](media/version-control-vcTabs.png)

瀏覽 [版本控制] > [Review Solution and Commit] (檢閱方案並認可) 功能表項目，以檢閱專案中的所有變更：

![檢閱方案](media/version-control-vcStatus.png)

這允許使用 [還原]、[建立修補檔案] 或 [認可] 的選項來檢視專案之每個檔案中的所有變更。

若要將檔案認可到遠端存放庫，請按 [認可...]，並輸入認可訊息，然後使用 [認可] 按鈕確認：

![認可檔案](media/version-control-svnCommit.png)

這會將變更傳送至存放庫，而它們會在其中建立您的所有修改的新修訂。

## <a name="see-also"></a>請參閱

- [設定 Subversion 存放庫](set-up-subversion-repository.md)
