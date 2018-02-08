---
title: "Visual Studio 訂閱 - 從 VLSC 重新傳送指派電子郵件"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend subscription assignment emails from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 338ae08ee1f3e6a819a1faea7bd095c9acd8ecd2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-within-volume-license-service-center-vlsc"></a>如何從大量授權服務中心 (VLSC) 內重新傳送訂閱指派電子郵件

有時候，被指派訂閱的訂閱者會要求系統管理員協助將其訂閱指派通知電子郵件重新傳送給他們。  在新的訂閱管理入口網站 (https://manage.visualstudio.com) 中，只要透過簡單的程序便能完成此動作。  不過，如果您的組織仍然在使用大量授權服務中心 (VLSC)，目前並沒有可自動重新傳送通知電子郵件的功能。  

若要從 VLSC 內重新傳送指派通知電子郵件，系統管理員必須使用下列因應措施：

## <a name="resending-the-assignment-email"></a>重新傳送指派電子郵件：

若要讓 VLSC 產生新的通知，必須在相同的交易上編輯訂閱者的電子郵件資訊，然後再將它變更回原本的電子郵件。 這將會使 VLSC 做出和指派新訂閱相同的反應，並再次傳送指派電子郵件。

1.  造訪[大量授權服務中心 (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) 並登入。
2.  按一下 [訂閱] 索引標籤，然後選擇 [Visual Studio 訂閱]。
3.  按一下與該 Visual Studio 訂用帳戶關聯的 [合約編號]。
4.  按一下 [搜尋] 列上的向下箭號。 
5.  使用 [電子郵件地址] 欄位搜尋訂閱者。
6.  在搜尋結果中找到該訂閱者，然後按一下其姓氏。 
7.  按一下 [編輯] 。
8.  編輯訂用帳戶。 例如，從訂閱者的電子郵件地址移除一個字元。 按一下 [儲存] 按鈕。
9.  當資訊儲存之後，再次按一下 [編輯]，復原剛才所做出的變更，然後按一下 [儲存]。  

這會使系統將該訂閱判斷為新的指派，並將指派通知電子郵件重新傳送給訂閱者。  