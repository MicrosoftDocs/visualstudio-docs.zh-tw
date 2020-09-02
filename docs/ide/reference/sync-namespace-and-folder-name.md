---
title: 同步命名空間和資料夾名稱
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d7073edaf6ecc261c58bf1e5607323b9214c5ed0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67160754"
---
# <a name="sync-namespace-and-folder-name"></a>同步命名空間和資料夾名稱

此重構適用於：

- C#

事項 **：** 同步命名空間和資料夾名稱。

時機 **：** 您想要藉由將檔案拖曳至新資料夾，來重新架構方案的各部分。 

**原因：** 您想要確保您的命名空間能以新的資料夾結構保持最新狀態。

## <a name="how-to"></a>操作方式

1. 將游標放在命名空間名稱中。
2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [**將命名 \<folder name> 空間變更為**]。

   ![同步命名空間和資料夾名稱](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
