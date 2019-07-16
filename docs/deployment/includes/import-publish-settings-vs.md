---
ms.openlocfilehash: 8adac174fbc78778e7154a205088fb9e9a57ae4a
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68143533"
---

1. 在您已於 Visual Studio 中開啟 ASP.NET 專案的電腦上，以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [發行]  。

1. 如果您之前已設定任何發行設定檔，[發行]  窗格會隨即出現。 按一下 [建立新設定檔]  。

1. 在 [挑選發行目標]  對話方塊中，按一下 [匯入設定檔]  。

    ![選擇 [發行]](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. 巡覽至您在上一節中所建立發行設定檔的位置。

1. 在 [匯入發行設定檔]  對話方塊中，巡覽至您在上一節中建立的設定檔並加以選取，然後按一下 [開啟]  。

    Visual Studio 隨即開始部署程序，而 [輸出] 視窗會顯示進度和結果。

    如果您收到任何部署錯誤，請按一下 [設定]  來編輯設定。 修改設定，並按一下 [驗證]  來測試新的設定。 如果找不到主機名稱，請嘗試使用 IP 位址，而不是 [伺服器]  和 [目的地 URL]  欄位中的主機名稱。

    ![在 [發行] 工具中編輯設定](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
