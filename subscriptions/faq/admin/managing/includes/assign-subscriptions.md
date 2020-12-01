---
title: 我要如何指派 Visual Studio 訂閱？
description: 您可以一次將訂閱指派給終端使用者，或使用「大量新增」功能快速並輕鬆上傳大量...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 09/30/2020
ms.openlocfilehash: add0bac2a9e7eb053c183d66fcee17c8133bb921
ms.sourcegitcommit: 593bdd2da62633f8d1f1eef70d0238e2682f3e02
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "91838441"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>我要如何指派 Visual Studio 訂閱？

您可以一次將訂閱指派給終端使用者，或使用「大量新增」功能快速並輕鬆地一次上傳大量的訂閱者。

個別指派訂閱：

1. 在 [manage.visualstudio.com](https://manage.visualstudio.com) 上，選取頁面頂端的[管理訂閱者](https://manage.visualstudio.com/subscribers)索引標籤
2. 選取 [新增]，然後輸入您要指派訂閱之使用者的名稱與電子郵件地址。
    1. 如果您的組織使用 Azure Active Directory，[名稱] 欄位會搜尋以尋找目前目錄中的人員。 您可以從搜尋結果中選取，或手動新增某人。
3. 如果您想要讓此訂閱者在登入 [Visual Studio 訂閱入口網站](https://my.visualstudio.com/)時可存取軟體下載，請務必將 [下載設定] 區段的 [下載] 切換按鈕維持為啟用狀態。
4. 完成 [通訊喜好設定] 區段，讓我們知道要使用哪些語言將指派電子郵件傳送給您的訂閱者。
5. 如果您想要新增與指派相關聯的任何附註，請使用 [參考] 選取項目。
6. 選取飛出面板底部的 [新增]，完成您的訂閱指派。 您的訂閱者將會收到一封電子郵件，並可立即開始使用其 Visual Studio 訂閱 (您的訂閱者不需要啟用)。

大量指派訂閱：

1. 在 [manage.visualstudio.com](https://manage.visualstudio.com) 上，選取頁面頂端的[管理訂閱者](https://manage.visualstudio.com/subscribers)索引標籤。
2. 選取 [大量新增]、下載 Excel 範本，然後儲存本機複本。
3. 所有欄位都是必要的，但 [參考] 欄位除外。
    1. 確定表單欄位未包含逗號。
    2. 移除表單欄位前後的空格。
    3. 請確定使用者名稱在兩段式名字或姓氏之間未包含額外的空格 (例如，如果某人的姓氏有兩個部分，如 "Maggie May"，應該輸入為 "MaggieMay")。
4. 返回 [manage.visualstudio.com](https://manage.visualstudio.com)，選取 [大量新增]，然後上傳您已儲存的 Excel 範本複本。
5. 上傳成功時，您會看到確認頁面，而您的訂閱者清單會填入您的新訂閱者。 您的訂閱者將會收到一封電子郵件，並可立即開始使用其 Visual Studio 訂閱 (您的訂閱者不需要啟用)。

若要深入了解如何快速且輕鬆地指派訂用帳戶，請參閱[在 Visual Studio 訂閱管理員入口網站中指派訂用帳戶](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) \(部分機器翻譯\)。  深入了解如何[管理含 GitHub Enterprise 訂用帳戶的 Visual Studio](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) \(部分機器翻譯\)。 

## <a name="what-is-the-github-enterprise-setup-process"></a>什麼是 GitHub Enterprise 設定程序？ 

GitHub Enterprise 是與 Visual Studio 訂用帳戶分開設定及管理的。 在購買含 GitHub Enterprise 的 Visual Studio 之後，會在於 manage.visualstudio.com 中建立合約時以平行 (但分開) 的方式起始 GitHub Enterprise 帳戶設定程序。 建立此 GitHub Enterprise 帳戶可能需要一些時間。  

在您的公司設定 GitHub Enterprise 帳戶之後，已獲指派含 GitHub Enterprise 訂用帳戶之 Visual Studio 的訂閱者將會收到來自 GitHub 的電子郵件，通知他們其 Visual Studio 訂用帳戶已連結。 當訂閱者收到這封電子郵件之後，他們就可以與其 GitHub 組織系統管理員聯繫，以接收適當組織的邀請。 

深入了解如何[管理含 GitHub Enterprise 訂用帳戶的 Visual Studio](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) \(部分機器翻譯\)。 如需 GitHub Enterprise 設定程序的其他詳細資料，請參閱[訂閱者文件](https://docs.microsoft.com/visualstudio/subscriptions/access-github) \(部分機器翻譯\)。 