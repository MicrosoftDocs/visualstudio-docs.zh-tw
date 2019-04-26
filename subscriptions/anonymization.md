---
title: 將 Visual Studio 訂閱者資料匿名化 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 10/31/2018
ms.topic: conceptual
description: 了解無法存取訂用帳戶時，訂閱者資料的匿名方式。
searchscope: VS Subscription
ms.openlocfilehash: a4249aa2520df6e9c1870fec121de2fdb2135308
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946197"
---
# <a name="anonymization-of-visual-studio-subscriber-information"></a>將 Visual Studio 訂閱者資訊匿名化

發生禁止訂閱者使用訂用帳戶的事件時 (例如訂用帳戶到期或刪除訂閱者的登入帳戶)，使用者的個人資訊 (例如名稱和登入帳戶) 基本上會變碼使其無法使用。  這麼做是為了保護訂閱者的個人資訊。

[!INCLUDE [GDPR-related guidance](includes/gdpr-intro-sentence.md)]

## <a name="when-does-anonymization-occur"></a>何時發生匿名化？

使訂閱者無法使用訂用帳戶的事件會觸發匿名化。  匿名化發生速度取決於訂用帳戶與觸發事件的類型。 如需詳細資訊，請參閱下表。

| 訂用帳戶類型                                                                                                                       | 事件觸發匿名化                                                                                                     | 何時發生匿名化 |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|---------------------------|
| Visual Studio Dev Essentials                                                                                                            | 訂閱者選擇不使用該程式，或不接受使用條款                                    | 30 天               |
| 透過 Microsoft Store (零售) 購買的 Visual Studio 訂用帳戶                                                                      | 訂用帳戶到期或未啟動                                                                   | 360 天                  |
| 透過大量授權、Visual Studio Marketplace (雲端訂用帳戶) 或 MPN 等程式取得的 Visual Studio 訂用帳戶 | 訂用帳戶到期或未指派給使用者                                                          | 180 天                  |
| 所有訂用帳戶                                                                                                                       | 已關閉用來登入訂用帳戶的 Azure Active Directory 帳戶或 Microsoft 帳戶 (MSA) | 立即               |
| 所有訂用帳戶                                                                                                                       | 從與 Azure Active Directory 帳戶建立關聯的租用戶中移除訂閱者                                | 立即               |

## <a name="faq"></a>常見問題集

### <a name="q--does-the-anonymization-of-the-subscribers-personal-information-cause-them-to-lose-access-to-the-subscription"></a>問：訂閱者的個人資訊匿名化會導致其無法存取訂用帳戶嗎？
答：否。  匿名化會回應導致無法存取訂用帳戶的事件，但並不會導致缺乏存取權。

### <a name="q--im-an-administrator-for-my-organizations-subscriptions--if-one-of-my-subscribers-information-is-anonymized-can-that-subscription-be-reassigned-to-another-user"></a>問：我是組織訂用帳戶的系統管理員。  如果訂閱者的其中一項資訊已匿名化，可以將該訂用帳戶重新指派給另一位使用者嗎？
答：可以，只要訂用帳戶尚未過期，可以將其重新指派給另一位訂閱者。

## <a name="next-steps"></a>後續步驟

了解如何透過[連結 MSA 與 AAD 身分識別](/azure/active-directory/b2b/add-users-administrator)來禁止匿名化。
