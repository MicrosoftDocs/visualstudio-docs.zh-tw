---
title: 版本控制
description: 在 Visual Studio for Mac 中使用 Git 和 Subversion。
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 0505177e01afd701fe5506df7dd0fc2a2e1f859c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965512"
---
# <a name="version-control"></a>版本控制

版本控制是管理許多不同版本之檔案的系統，而且在軟體開發中，通常是由許多開發人員提供。 任何版本控制系統的主要目的 (_VCS_) 都是尋找方案，讓所有使用者同時處理程式碼基底。

任何版本控制系統的核心都是「存放庫」，可作為所有不同檔案的中央資料存放區，並與檔案伺服器類似。 不過，與檔案伺服器不同，存放庫包含專案的整個歷程記錄以及所有已進行的修訂。

如果存放庫是中央資料存放區，則每位使用者邏輯上都會有資料的本機存放區，可讓他們進行處理。 這稱為「工作複本」。 在 Visual Studio for Mac 中，您的工作複本將會顯示為電腦上的任何其他本機目錄，讓您可以讀取和寫入任何檔案。 不過，因為 Visual Studio for Mac 具有版本控制系統整合，所以您可以在不需要離開 IDE 的情況下使用 Subversion 和 Git。

Subversion 是集中式的版本控制系統，這表示會有包含所有檔案和修訂的單一伺服器，而使用者可以從中簽出任何檔案的任何版本。 從遠端 Subversion 存放庫簽出檔案時，使用者會收到存放庫在該時間點的快照集。

Git 是一種分散式版本控制系統，可讓小組同時處理相同的文件。 Git 可能也會有包含所有檔案的單一伺服器，差異在於每當從這個中央來源簽出存放庫時，系統就會將整個存放庫本機複製至您的電腦。

## <a name="basic-concepts"></a>基本概念

Visual Studio for Mac 同時支援 Git 和 Subversion 版本控制系統。 下面的文章會探討如何透過 Visual Studio for Mac 設定 Git 和 Subversion 存放庫，以及檢閱、認可和推送變更這類簡單功能。

* [設定 Git 存放庫](set-up-git-repository.md)
* [使用 Git](working-with-git.md)
* [設定 Subversion 存放庫](set-up-subversion-repository.md)
* [使用 Subversion](working-with-subversion.md)

## <a name="see-also"></a>另請參閱

* [Visual Studio 中的版本控制 (Windows 上)](/visualstudio/version-control/)