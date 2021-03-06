---
ms.openlocfilehash: 94c2c733b631ef5e727c79a6e093bb224aec38c4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249920"
---

1. 在您已於 Visual Studio 中開啟 ASP.NET 專案的電腦上，以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [發行]。

   如果您之前已設定任何發行設定檔，[發行] 窗格會隨即出現。 按一下 [ **新增** ] 或 [ **建立新的設定檔**]。

1. 選取匯入設定檔的選項。

   ::: moniker range=">=vs-2019"
   在 [ **發行** ] 對話方塊中，按一下 [匯 **入設定檔**]。
   ::: moniker-end
   ::: moniker range="vs-2017"
   在 [挑選發行目標] 對話方塊中，按一下 [匯入設定檔]。
   ::: moniker-end

   ![選擇 [發行]](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. 巡覽至您在上一節中所建立發行設定檔的位置。

1. 在 [匯 **入發行設定檔** ] 對話方塊中，流覽至您在上一節中建立的設定檔並加以選取，然後按一下 [ **開啟**]。

   ::: moniker range=">=vs-2019"
   按一下 **[完成]** 儲存發行設定檔，然後按一下 [ **發佈**]。

   Visual Studio 隨即開始部署程序，而 [輸出] 視窗會顯示進度和結果。

   如果您收到任何部署錯誤，請按一下 [ **編輯** ] 以編輯設定。 修改設定，並按一下 [驗證] 來測試新的設定。 如果找不到主機名稱，請嘗試使用 IP 位址，而不是 [伺服器] 和 [目的地 URL] 欄位中的主機名稱。
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio 隨即開始部署程序，而 [輸出] 視窗會顯示進度和結果。

   如果您收到任何部署錯誤，請按一下 [設定] 來編輯設定。 修改設定，並按一下 [驗證] 來測試新的設定。 如果找不到主機名稱，請嘗試使用 IP 位址，而不是 [伺服器] 和 [目的地 URL] 欄位中的主機名稱。
   ::: moniker-end

   ![在 [發行] 工具中編輯設定](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
