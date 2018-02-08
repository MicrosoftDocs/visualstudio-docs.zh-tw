---
title: "如何從 VLSC 重新傳送訂用帳戶指派電子郵件 | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 12/29/2017
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to a subscriber from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 7162435044a578a94249774305f2c6b8b6438219
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-vlsc"></a>如何從 VLSC 重新傳送訂用帳戶指派電子郵件：

當訂用帳戶被指派給 VLSC 中的訂閱者且訂閱者要求傳送指派電子郵件時，您可以編輯訂閱者的電子郵件資訊並將它變更回原始地址，以完成此作業。 這將會自動觸發指派電子郵件的重新傳送。

請依照下列指示重新傳送指派電子郵件：


1. 瀏覽大量授權服務中心 (VLSC) 並登入。
2. 從 VLSC [系統管理] 頁面，按一下 [訂用帳戶]，然後按一下 [Visual Studio 訂用帳戶]。
3. 按一下與該 Visual Studio 訂用帳戶關聯的 [合約編號]。
4. 按一下 [搜尋] 列上的向下箭號。  
5. 使用 [電子郵件地址] 欄位搜尋訂閱者。
6. 從結果清中，按一下 [訂閱者] 上的 [姓氏]。
7. 按一下 [編輯]。
8. 編輯訂用帳戶。 要針對哪個項目進行變更並不重要，重要的是進行變更。  例如，從訂閱者的電子郵件地址移除一個字元 (將 “m” 從 .com 移除)。按一下 [儲存] 按鈕
9. 儲存資訊之後，再次按一下 [編輯] 按鈕並修正電子郵件地址中缺少的字元。 按一下 [儲存]。
   
這會使得 VLSC 發現訂用帳戶發生變更，並重新傳送指派電子郵件給入口網站上所列的電子郵件。 

> [!NOTE]
> - 新指派的訂用帳戶將會自動產生指派電子郵件。 只有當使用者要求新的指派電子郵件通知或通知因為任何原因而未傳送時，才需要執行上面的動作。
> - 透過 https://manage.visualstudio.com 重新傳送所指派訂用帳戶的指派電子郵件時，不需要執行此程序。若要在入口網站中重新傳送指派電子郵件給訂閱者，只要選取訂閱者，並按一下訂用帳戶清單上方的 [重新傳送] 按鈕。  