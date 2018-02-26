---
title: "如何從 Manage.visualstudio.com 或 VLSC 內重新傳送訂用帳戶指派電子郵件 | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 2/13/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to subscribers from manage.visualstudio.com or VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 0ba7d6e36c25ced78b0c6b25688e5eb5b26eb04a
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="how-to-resend-subscription-assignment-emails"></a>如何重新傳送訂用帳戶指派電子郵件：

重新傳送指派電子郵件所需的步驟會隨您用來管理訂用帳戶的入口網站而不同。 

## <a name="resending-assignment-emails-from-within-managevisualstudiocom"></a>從 manage.visualstudio.com 內重新傳送指派電子郵件

從 manage.visualstudio.com 入口網站內重新傳送指派電子郵件的程序非常簡單：

1. 瀏覽 [manage.visualstudio.com](https://manage.visualstudio.com) 入口網站並登入。 
2. 使用 [篩選] 索引標籤搜尋要重新傳送指派電子郵件的訂閱者 (如需有關篩選的詳細資訊，請參閱[搜尋訂用帳戶](/visualstudio/subscriptions/search-license))。
3. 在訂閱者上按一下。  您可以使用 Ctrl+按一下或 Shift+按一下來選取多個訂閱者。
4. 按一下搜尋結果頂端的 [重新傳送]。  

## <a name="resending-assignment-emails-from-within-vlsc"></a>從 VLSC 內重新傳送指派電子郵件
當訂用帳戶被指派給 VLSC 中的訂閱者且訂閱者要求傳送指派電子郵件時，您可以編輯訂閱者的電子郵件資訊並將它變更回原始地址，以完成此作業。 這將會自動觸發指派電子郵件的重新傳送。

請依照下列指示重新傳送指派電子郵件：


1. 瀏覽大量授權服務中心 (VLSC) 並登入。
2. 從 VLSC [系統管理] 頁面，按一下 [訂用帳戶]，然後按一下 [Visual Studio 訂用帳戶]。
3. 按一下與該 Visual Studio 訂用帳戶關聯的 [合約編號]。
4. 按一下 [搜尋] 列上的向下箭號。  
5. 使用 [電子郵件地址] 欄位搜尋訂閱者。
6. 從結果清中，按一下 [訂閱者] 上的 [姓氏]。
7. 按一下 [編輯] 。
8. 編輯訂用帳戶。 要針對哪個項目進行變更並不重要，重要的是進行變更。  例如，從訂閱者的電子郵件地址移除一個字元 (將 “m” 從 .com 移除)。按一下 [儲存] 按鈕
9. 儲存資訊之後，再次按一下 [編輯] 按鈕並修正電子郵件地址中缺少的字元。 按一下 [儲存] 。
   
這會使得 VLSC 發現訂用帳戶發生變更，並重新傳送指派電子郵件給入口網站上所列的電子郵件。 

> [!NOTE]
> - 新指派的訂用帳戶將會自動產生指派電子郵件。 只有當使用者要求新的指派電子郵件通知或通知因為任何原因而未傳送時，才需要執行上面的動作。
