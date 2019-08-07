---
title: 開始使用訂閱系統管理入口網站 | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: 了解如何開始使用訂閱系統管理入口網站管理組織的 Visual Studio 訂閱。
ms.openlocfilehash: f3b11a0a0977fff8a6c89f565adffb1cac49e2ad
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605731"
---
# <a name="get-started-with-the-visual-studio-subscriptions-administration-portal"></a>開始使用 Visual Studio 訂閱系統管理入口網站
使用 Visual Studio 訂用帳戶管理入口網站時，請牢記：
- **Visual Studio 訂用帳戶依使用者授權。** 每位訂閱者可以基於開發和測試用途在任意數量的電腦上使用軟體。
- 根據貴組織購買的 Visual Studio 訂用帳戶，**僅為每位訂閱者指派一個訂用帳戶層級**。 如果您的訂閱者獲派超過一個以上的訂閱等級，請編輯他們的設定，讓他們只擁有一個等級。
- 如果升級訂閱 (在購買「升級」授權之後) 或以較低等級續訂，**也必須更新訂閱者的訂用帳戶等級**。
- **請勿讓訂閱者彼此共用訂用帳戶。** 訂閱必須指派給具名的個人。  不允許將訂閱指派給小組。  您必須將訂用帳戶指派給使用全部或部分訂用帳戶權益的任一人 (供開發和測試用的軟體、Microsoft Azure、E-learning 等等)。

## <a name="access-to-the-portal"></a>存取入口網站
如果您是組織合約的主要連絡人或通知連絡人，系統會在您設定大量授權合約時，自動布建入口網站的存取權給您。 您會收到系統觸發的歡迎電子郵件，且郵件中會指出要使用哪一個電子郵件地址登入入口網站。 登入之後，系統會自動將您設定為超級系統管理員，並且可以開始管理訂閱和其他系統管理員。 

## <a name="administrator-roles"></a>系統管理員規則
大量授權客戶的新 Visual Studio 訂用帳戶管理入口網站中有兩個不同的角色。 這些角色像是目前 VLSC 中的主要/通知連絡人角色和訂用帳戶管理員角色。

**超級管理員：** 第一次設定組織時，主要或通知連絡人預設會成為超級管理員。 主要或通知連絡人可以選擇指派其他的超級管理員或系統管理員。 超級管理員可以新增和移除其他系統管理員以及訂閱者。 如果系統中有兩個以上的超級管理員，則超級管理員可以刪除所有超級管理員，但最後必須保留兩個以策安全。

**系統管理員：** 系統管理員只能由超級管理員設定。系統管理員可以管理超級管理員在合約中指派給他們的訂閱者。

## <a name="the-subscribers-page"></a>訂閱者頁面
一旦指派了訂用帳戶，[訂閱者] 索引標籤就會提供訂閱者的詳細資訊，包括：
- 每位訂閱者的姓名。
- 此使用者的電子郵件地址。
- 已指派給他們的訂用帳戶層級。
- 訂用帳戶指派給他們的日期。
- 訂用帳戶到期日。
- 選擇性的文字描述。
- 指出訂閱者下載啟用或停用。
- 他們所在的國家/地區。
- 他們在管理入口網站指派通訊電子郵件的語言設定。
- 選擇性欄位，用於登入通訊以外的其他電子郵件地址。

在此頁面的左側，您可以看到已購買、指派，及貴組織每份合約仍然可用的訂用帳戶授權數目等其他資訊。
> [!div class="mx-imgBorder"]
> ![Visual Studio 訂用帳戶管理入口網站訂閱者頁面](_img/using-admin-portal/subscribers-page.png)

## <a name="the-details-page"></a>詳細資料頁面
如需目前檢視的合約詳細資訊，請選取 [詳細資料] 索引標籤。它會顯示合約狀態、購買帳戶、組織詳細資料、超級系統管理員和其他相關資訊。
> [!div class="mx-imgBorder"]
> ![Visual Studio 訂用帳戶管理入口網站詳細資料頁面](_img/using-admin-portal/details-page.png)

## <a name="next-steps"></a>後續步驟
深入了解系統管理員的責任：
- [系統管理員責任概觀](admin-responsibilities.md)
- [清查生產前環境](admin-inventory.md)
- [管理大型小組及外部承攬人](manage-teams.md)
- [追蹤使用者指派及處理訂單](assignments-orders.md)
- 使用[使用量上限](maximum-usage.md)來追蹤購買承諾用量
