---
title: "WhiteSource Bolt 權益"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: "了解如何啟用 Visual Studio 訂用帳戶所含的 WhiteSource Bolt 訂用帳戶。"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: c1976d9eaa6ef18978a9e9d5453c3080741223d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
#  <a name="activating-the-whitesource-bolt-benefit-in-visual-studio-subscriptions"></a>啟用 Visual Studio 訂用帳戶的 WhiteSource Bolt 權益

找出並修正開放原始碼弱點，以及產生組建中所有開放原始碼元件的全面清查及授權報表。  Enterprise 訂用帳戶包含六個月免費訂用帳戶。 

1.  若要使用 WhiteSource Bolt 權益，請按一下權益磚底部的 [Get Code] (取得代碼) 連結。    

![WhiteSource 權益磚](_img\vs-whitesource\vs-whitesource-tile.png)

2.  您會收到顯示啟用代碼的通知。  **將程式碼複製至剪貼簿**，然後按一下 [啟用]。 

![WhiteSource 權益程式碼 ](_img\vs-whitesource\vs-whitesource-code.png)

3.  在 WhiteSource 網頁上，按一下 [啟用] 按鈕，或向下捲動至頁面的 [啟用您的帳戶] 區段。  

![WhiteSource 權益啟用](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  在頁面的 [啟用您的帳戶] 區段中，將會引導您完成四個步驟：
- 從 Microsoft Visual Studio Marketplace 中，[安裝](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) WhiteSource Bolt 延伸模組。 如果您沒有安裝延伸模組的權限，請前往[本頁面](https://www.visualstudio.com/en-us/docs/marketplace/get-vsts-extensions#request)。

    如果您要使用 VSTS，請按一下綠色 [安裝] 按鈕，或 Team Foundation Server 的 [下載] 按鈕。  在此範例中，我們將使用 VSTS。 

![WhiteSource 權益安裝延伸模組](_img\vs-whitesource\vs-whitesource-download-install.png)

- 接下來，選取您想要使用的 VSTS 帳戶，然後按一下 [確認]   (如果您尚未設定 VSTS，請前往[權益](https://my.visualstudio.com/benefits)頁面，然後啟用 VSTS 權益)。

![WhiteSource 權益確認帳戶](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- 您會收到延伸模組已安裝並可供使用的確認。  按一下 [開始使用]，返回 WhiteSource Bolt 頁面繼續進行。  

![WhiteSource 權益安裝完成](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  開啟 Visual Studio Team Services (VSTS) 專案儀表板，並按一下 [Build & Releas] (建置和發行) 功能表，然後選擇 [WhiteSource Bolt]。

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
