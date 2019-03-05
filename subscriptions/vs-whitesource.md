---
title: WhiteSource Bolt 權益 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 12/19/2018
ms.topic: conceptual
description: 了解如何啟用 Visual Studio 訂用帳戶所含的 WhiteSource Bolt 訂用帳戶。
searchscope: VS Subscription
ms.openlocfilehash: 482f0e5054b1b2ad7ea677b40d5d368004227ec8
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842191"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>Visual Studio 訂用帳戶中的 WhiteSource Bolt

找出並修正開放原始碼弱點，以及產生組建中所有開放原始碼元件的全面清查及授權報表。 某些 Visual Studio 訂用帳戶包含六個月的免費存取。

## <a name="activation-steps"></a>啟用步驟

1. 若要啟用 WhiteSource Bolt 優點，請登入 [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs)。

2. 在 [工具] 區段找到 [WhiteSource Bolt] 磚，並按一下權益磚底部的 [取得代碼] 連結。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 權益磚](_img/vs-whitesource/vs-whitesource-tile.png)

3. 您會收到顯示啟用代碼的通知。  **將程式碼複製至剪貼簿**，然後按一下 [啟用]。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 權益程式碼](_img/vs-whitesource/vs-whitesource-code.png)

4. 在 WhiteSource 網頁上，按一下 [啟用] 按鈕，或向下捲動至頁面的 [啟用您的帳戶] 區段。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 權益啟用](_img/vs-whitesource/vs-whitesource-activate-page-cropped.png)

5. 在頁面的 [啟用您的帳戶] 區段中，將會引導您完成四個步驟：

   - 從 Microsoft Visual Studio Marketplace 中，[安裝](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) WhiteSource Bolt 延伸模組。 如果您沒有權限可以安裝延伸模組，請參閱[安裝 Azure DevOps Services 的免費延伸模組](/azure/devops/marketplace/install-vsts-extension?view=vsts)。


如果您要使用 Azure DevOps Services，請按一下綠色 [安裝] 按鈕，或 Team Foundation Server 的 [下載] 按鈕。  在此範例中，我們將使用 Azure DevOps Services。
> [!div class="mx-imgBorder"]
> ![WhiteSource 權益安裝延伸模組](_img/vs-whitesource/vs-whitesource-download-install.png)

- 接下來，選取您希望使用的 Azure DevOps 組織，然後按一下 [確認]。  (如果尚未設定 Azure DevOps Services，請前往[權益](https://my.visualstudio.com/benefits)頁面並啟用您的 Azure DevOps Services 權益。)

> [!div class="mx-imgBorder"]
> ![WhiteSource 權益確認帳戶](_img/vs-whitesource/vs-whitesource-confirm-account.png)

- 您會收到延伸模組已安裝並可供使用的確認。  按一下 [開始使用]，返回 WhiteSource Bolt 頁面並繼續。
> [!div class="mx-imgBorder"]
> ![WhiteSource 權益安裝完成](_img/vs-whitesource/vs-whitesource-install-complete.png)

5. 開啟您的 Azure DevOps 專案儀表板，按一下 [Azure Pipelines] 功能表，然後選擇 [WhiteSource Bolt]。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 權益新增延伸模組](_img/vs-whitesource/vs-whitesource-installed-cropped.png)

6. 從 WhiteSource Bolt 權益磚貼上啟用代碼，然後按一下 [啟用]。 每個啟用代碼都只能用來啟用一個專案。
   > [!div class="mx-imgBorder"]
   > ![WhiteSource 權益啟用碼](_img/vs-whitesource/vs-whitesource-activate-code-cropped.png)

7. 您的啟用現在已完成，而且您的訂用帳戶目前還有 180 天。

8. 您需要將 WhiteSource Bolt 延伸模組新增為其中一個建置步驟。  [WhiteSource Bolt 頁面](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate)上提供顯示做法的影片。

9. 執行組建之後，就會自動產生下列完整的報表和儀表板：
    - 安全性弱點儀表板
    - 安全性弱點報表
    - 過時的程式庫報表
    - 授權風險和相容性儀表板
    - 清查報表

## <a name="eligibility"></a>資格

| 訂用帳戶層級                                                 |     通道                                            | 優勢                                                          | 可續約？    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, 零售, 選取的 NFR<sup>1</sup> | 6 個月       |  是          |
| Visual Studio Professional (Standard) | VL, Azure, 零售                                       | 無法使用                                                           |NA         |
| Visual Studio Test Professional (標準訂用帳戶)                         | VL, 零售                                              | 無法使用                                             |  NA         |
| MSDN 平台 (標準)                                          | VL, 零售                                              | 無法使用                                              | NA         |
| Visual Studio Dev Essentials | NA  | 無法使用 |NA |
| Visual Studio Enterprise、Visual Studio Professional (每月雲端) | Azure                                       | 無法使用                                                           |NA|

<sup>1</sup>  *包含：Microsoft 合作夥伴網路 (Enterprise)。排除：其他禁止轉售 (NFR)、Visual Studio 產業夥伴 (VSIP)、FTE、MCT 軟體與服務開發人員、BizSpark、Imagine、最有價值專家 (MVP)、區域經理 (RD)、MCT 軟體與服務、Microsoft 合作夥伴網路 (專業版)。*


> [!NOTE]
> Microsoft 不再於雲端訂用帳戶中提供 Visual Studio Professional 年度訂用帳戶和 Visual Studio Enterprise 年度訂用帳戶。 現有的客戶體驗，以及更新、增加、減少或取消其訂用帳戶的能力將不會改變。 我們鼓勵新的客戶移至 [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) 來探索 Visual Studio 的不同購買選項。


不確定您使用哪一個訂用帳戶？  連線到 [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) 以查看指派給您的電子郵件地址的所有訂用帳戶。 若沒有看到您的所有訂用帳戶，可能有一或多個訂用帳戶是指派到不同的電子郵件地址。  您必須以該電子郵件地址登入才能查看對應的訂用帳戶。

## <a name="support-resources"></a>支援資源

-  需要 WhiteSource Bolt 的說明嗎？  在 https://www.whitesourcesoftware.com/vse_whitesource_bolt/ 與 WhiteSource Bolt 代表即時聊天
-  如需 Visual Studio 訂用帳戶有關銷售、訂閱、帳戶與計費的協助，請聯繫 Visual Studio [訂用帳戶支援](https://visualstudio.microsoft.com/subscriptions/support/)。
-  是否有關於 Visual Studio IDE、Azure DevOps Services 或其他 Visual Studio 產品或服務的問題？  前往 [Visual Studio 支援](https://visualstudio.microsoft.com/support/)