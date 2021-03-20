---
title: 將新的每月訂閱新增至訂用帳戶管理入口網站 |Microsoft 檔
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 03/19/2021
ms.topic: how-to
description: 瞭解如何在訂用帳戶管理入口網站中，新購買的每月 Visual Studio 訂閱
ms.openlocfilehash: 931f297a650926e4da5c13271a58091c9f00ddd3
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757642"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>將新的每月 Visual Studio 訂用帳戶新增至訂用帳戶管理入口網站
當您使用 Azure 訂用帳戶購買新的每月 Visual Studio 訂用帳戶時，您可能需要將這些訂用帳戶新增至訂用帳戶管理入口網站，才能將它們指派給使用者。  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>如何? 知道我是否需要新增我的訂閱嗎？
新增每月訂閱的步驟取決於您的組織已擁有的訂閱種類，以及您是否為新的系統管理員。
- 如果您是新的系統管理員，我們會在您第一次登入訂用帳戶管理入口網站時，檢查您有使用者存取系統管理員許可權的 Azure 訂用帳戶。  如果我們找到每月訂閱，我們會自動新增。 
- 如果您先前已新增或管理每月訂用帳戶，我們會在您每次登入時檢查新的每月訂閱。 
- 如果您已經是透過大量授權取得訂用帳戶的系統管理員，但先前尚未新增或受管理的每月訂用帳戶，您必須使用以下提供的步驟來新增這些訂閱。

## <a name="how-to-add-monthly-subscriptions"></a>如何新增每月訂閱
1. 登入訂用帳戶管理入口網站，網址為 <https://manage.visualstudio.com>
1. 在 [ **管理訂閱者** ] 索引標籤上，選擇 [ **新增合約** ] 下拉式清單 
1. 在下拉式清單中選擇 **新的每月訂閱**
   > [!div class="mx-imgBorder"]
   > ![加入新的每月訂閱下拉式清單](_img/add-monthly-subs/add-subs-drop-down.png "選擇 [新增合約]，然後選擇 [新的每月訂閱]。")
1. 系統會搜尋任何您具有「使用者存取系統管理員」許可權的 Azure 訂用帳戶，並將匯入使用這些 Azure 訂用帳戶購買的任何 Visual Studio 訂用帳戶。
1. 如果找不到具有使用者存取系統管理員許可權的 Azure 訂用帳戶，或找到符合資格的 Azure 訂用帳戶，但找不到任何 Visual Studio 訂用帳戶，您將會收到下列訊息：
   > [!div class="mx-imgBorder"]
   > ![找不到任何新的每月訂閱](_img/add-monthly-subs/no-subs-found.png "指出沒有 Azure 訂用帳戶或 Visual Studio 訂用帳戶可供您使用的錯誤訊息。")
1. 如果找到新的每月訂閱，您將會收到確認訊息
   > [!div class="mx-imgBorder"]
   > ![訂用帳戶已新增確認訊息](_img/add-monthly-subs/subs-added-confirmation.png "確認訊息將會顯示您已新增的訂用帳戶。")

## <a name="things-to-keep-in-mind"></a>要牢記在心的事項
- 新增每月訂閱的選項只有在您第一次購買時才可使用。  新增每月訂用帳戶之後，我們會在您每次登入入口網站時檢查是否有新的訂閱。 
- 當找到新的訂用帳戶時，您可能會看到這些訂閱已指派給訂閱者。  這是因為有其他系統管理員可以存取 Azure 訂用帳戶，而且他們已經將新的 Visual Studio 訂用帳戶指派給使用者。  現在您也已將它們新增至入口網站，您可以管理這些訂用帳戶。 

## <a name="support-resources"></a>支援資源
- 如需 Visual Studio 訂閱管理的協助，請聯絡 [Visual Studio 訂閱支援](https://aka.ms/vsadminhelp)。

## <a name="next-steps"></a>下一步
現在您已新增訂用帳戶，您已準備好將它們指派給使用者。  您可以透過數種方式來執行此動作：
- [個別指派訂用帳戶](assign-license.md)
- [指派訂閱給多個使用者](assign-license-bulk.md)
- [將特定訂閱指派給特定使用者](assign-guid.md)

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)