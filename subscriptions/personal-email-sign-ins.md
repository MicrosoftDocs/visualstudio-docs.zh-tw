---
title: "顯示於 VLSC 中的個人電子郵件"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: "Visual Studio Subscriptions – Why Am I Seeing Hotmail or Gmail Addresses for My Subscribers?"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 2bfe2f39d432be5fc6ff7b24be2a218d02fce961
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio 訂閱 – 我為何會針對我的訂閱者看見 Hotmail 或 Gmail 地址？ 

隨著公司從大量授權服務中心 (VLSC) 移轉至新的 Visual Studio [訂閱管理入口網站](https://manage.visualstudio.com)，系統管理員可能會對於部分訂閱者的「登入電子郵件地址」是顯示為第三方電子郵件地址 (例如 Hotmail、Gmail 或 Yahoo) 感到訝異。

## <a name="cause"></a>原因

此案例是因為與舊版 MSDN 訂閱者體驗相關聯的登入程序所造成。 使用者是在沒有被修改的情況下，從 VLSC 移轉至新的入口網站。 某些系統管理員可能沒有發現部分使用者一直都是使用個人帳戶來存取其訂閱權益。 在於 2016 年完成的 Visual Studio 訂閱者移轉之前，若要成功使用 Visual Studio 訂閱，必須完成兩項動作：
1. 系統管理員使用個別訂閱者的公司或學校電子郵件地址，將訂閱「指派」給他們。
2. 該訂閱者「啟動」訂閱。

在訂閱者啟動程序期間：
1. 需要使用 Microsoft 帳戶 (MSA) 來登入。
2. 若訂閱者沒有嘗試將其公司或學校帳戶 (例如 John@contoso.com) 轉換成 MSA，他們則可以建立新的 MSA 或使用現有的 MSA。
3. 這導致其「登入電子郵件地址」和「指派電子郵件地址」有所不同。

> [!NOTE] 
> [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) 上的新訂閱者體驗，同時支援公司/學校帳戶及 Microsoft 帳戶 (MSA) 身分識別類型。

最後，由於系統管理員移轉會使用來自 VLSC 有關訂閱者「登入電子郵件地址」的資料來填入新的訂閱者管理體驗，加上我們對新 UI 所做出的變更會使這些個人帳戶變得更加容易看見，因此於近期完成移轉的系統管理員可能會看見這些先前沒有注意到的資訊。

## <a name="solution"></a>方案

若要更正此問題，您必須編輯訂閱者資訊以更新其登入電子郵件地址。  您可以對單一訂閱者進行編輯，或是大量做出編輯。 如需完整資訊，請造訪[編輯訂閱](/visualstudio/subscriptions/edit-license)。  

在您更新訂閱者的電子郵件地址之後，便應該通知他們其登入資訊已經變更。  