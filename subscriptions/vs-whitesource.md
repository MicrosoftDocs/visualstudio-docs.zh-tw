---
title: "WhiteSource Bolt 權益 | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/11/2017
Ms.topic: Get-Started-Article
Description: Learn how to activate the WhiteSource Bolt subscription included with your Visual Studio subscription.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: fe8e731e26765ec17b56383e04362efa25b2f141
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>Visual Studio 訂用帳戶的 WhiteSource Bolt

## <a name="overview"></a>總覽

找出並修正開放原始碼弱點，以及產生組建中所有開放原始碼元件的全面清查及授權報表。  選取的 Visual Studio 訂用帳戶包含六個月的免費存取。 

## <a name="eligibility"></a>資格

| 訂用帳戶等級/方案                                                  | 優勢               | 可續約？                                                         |
|-------------------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------|
| Visual Studio Enterprise Standard                                             | 6 個月              | [是]                                                                |
| Visual Studio Enterprise 年度                                               | 6 個月              | [是]                                                                |
| Visual Studio Enterprise 每月                                              | 無法使用         |                                                                    |
| Visual Studio Professional Standard                                           | 無法使用         |                                                                    |
| Visual Studio Professional 年度                                             | 無法使用         |                                                                    | 
| Visual Studio Professional 每月                                            | 無法使用         |                                                                    |
| Visual Studio Test Pro                                                        | 無法使用         |                                                                    |
| MSDN 平台                                                                | 無法使用         |                                                                    |
| Visual Studio Dev Essentials                                                  | 無法使用         |                                                                    |
| Visual Studio Enterprise - NFR<sup>1</sup>                                               | 無法使用         |                                                                    |
| Visual Studio Enterprise - FTE                                                | 無法使用         |                                                                    |
| Visual Studio Enterprise - Microsoft 合作夥伴網路                          | 6 個月              | [是]                                                                |
| Visual Studio Professional - Microsoft 合作夥伴網路                        | 無法使用         |                                                                    |
| Visual Studio Enterprise – Imagine (Standard)                                 | 無法使用         |                                                                    |
| Visual Studio Enterprise – Imagine (Premium)                                  | 無法使用         |                                                                    |
| Visual Studio Enterprise – BizSpark                                           | 無法使用         |                                                                    |
| Microsoft 合格訓練人員 - 軟體與服務                             | 無法使用         |                                                                    |
| Microsoft 合格訓練人員 - 軟體與服務開發人員                   | 無法使用         |                                                                    |

<sup>1</sup>  *包括「禁止轉售」(NFR)、Microsoft Valued Partner (MVP)、Region Director (RD)、Visual Studio 產業夥伴 (VSIP)*  

不確定您使用哪一個訂用帳戶？  連線到 [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) 以查看指派至您電子郵件地址的所有訂用帳戶。 若沒有看到您的所有訂用帳戶，可能有一或多個訂用帳戶是指派到不同的電子郵件地址。  您必須以該電子郵件地址登入才能查看對應的訂用帳戶。 

## <a name="activation-steps"></a>啟用步驟

1.  若要啟用您的 WhiteSource Bolt 權益，請登入 [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs)。

2.  在 [工具] 區段找到 [WhiteSource Bolt] 磚，並按一下權益磚底部的 [取得代碼] 連結。    

    ![WhiteSource 權益磚](_img\vs-whitesource\vs-whitesource-tile.png)

2.  您會收到顯示啟用代碼的通知。  **將程式碼複製至剪貼簿**，然後按一下 [啟用]。 

    ![WhiteSource 權益程式碼 ](_img\vs-whitesource\vs-whitesource-code.png)

3.  在 WhiteSource 網頁上，按一下 [啟用] 按鈕，或向下捲動至頁面的 [啟用您的帳戶] 區段。  

    ![WhiteSource 權益啟用](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  在頁面的 [啟用您的帳戶] 區段中，將會引導您完成四個步驟：
    - 從 Microsoft Visual Studio Marketplace 中，[安裝](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) WhiteSource Bolt 延伸模組。 如果您沒有安裝延伸模組的權限，請前往[本頁面](https://www.visualstudio.com/docs/marketplace/get-vsts-extensions#request)。

    如果您要使用 VSTS，請按一下綠色 [安裝] 按鈕，或 Team Foundation Server 的 [下載] 按鈕。  在此範例中，我們將使用 VSTS。 

    ![WhiteSource 權益安裝延伸模組](_img\vs-whitesource\vs-whitesource-download-install.png)

    - 接下來，選取您想要使用的 VSTS 帳戶，然後按一下 [確認]   (如果您尚未設定 VSTS，請前往[權益](https://my.visualstudio.com/benefits)頁面，然後啟用 VSTS 權益)。

    ![WhiteSource 權益確認帳戶](_img\vs-whitesource\vs-whitesource-confirm-account.png)

    - 您會收到延伸模組已安裝並可供使用的確認。  按一下 [開始使用]，返回 WhiteSource Bolt 頁面並繼續。  

    ![WhiteSource 權益安裝完成](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  開啟 Visual Studio Team Services (VSTS) 專案儀表板，並按一下 [Build & Releas (建置和發行)] 功能表，然後選擇 [WhiteSource Bolt]。

    ![WhiteSource 權益新增延伸模組](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. 從 WhiteSource Bolt 權益磚貼上啟用代碼，然後按一下 [啟用]。 每個啟用代碼都只能用來啟用一個專案。 

    ![WhiteSource 權益啟用碼](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  您的啟用現在已完成，而且您的訂用帳戶目前還有 180 天。 

8.  您需要將 WhiteSource Bolt 延伸模組新增為其中一個建置步驟。  [WhiteSource Bolt 頁面](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate)上提供顯示做法的影片。  

9. 執行組建之後，就會自動產生下列完整的報表和儀表板：
    - 安全性弱點儀表板
    - 安全性弱點報表
    - 過時的程式庫報表
    - 授權風險和相容性儀表板
    - 清查報表

## <a name="faq"></a>常見問題集
到這裡查看是否有更新

## <a name="support-resources"></a>支援資源
-  需要 WhiteSource Bolt 的說明嗎？  與 WhiteSource Bolt 代表即時交談：https://www.whitesourcesoftware.com/vse_whitesource_bolt/ (英文) 
-  如需 Visual Studio 訂用帳戶有關銷售、訂閱、帳戶與計費的協助，請聯繫 Visual Studio [訂用帳戶支援](https://www.visualstudio.com/subscriptions/support/)。
-  是否有關於 Visual Studio IDE、Visual Studio Team Services 或其他 Visual Studio 產品或服務的問題？  前往 [Visual Studio 支援](https://www.visualstudio.com/support/) 

