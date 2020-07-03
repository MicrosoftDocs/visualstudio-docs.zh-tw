---
title: 將新的每月 Visual Studio 訂閱新增至訂用帳戶管理入口網站 |Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 06/23/2020
ms.topic: how-to
description: 瞭解如何在訂用帳戶系統管理入口網站中，新購買的每月 Visual Studio 訂閱
ms.openlocfilehash: 778a3adbc9ca2117b0328a10d52904921bd0b80c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904702"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>將新的每月 Visual Studio 訂用帳戶新增至訂閱系統管理入口網站
當您使用 Azure 訂用帳戶購買新的每月 Visual Studio 訂閱時，您可能需要將其新增至訂用帳戶管理入口網站，才能將它們指派給使用者。  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>如何? 知道我是否需要新增我的訂閱？
新增每月訂閱的步驟取決於您的組織已擁有的訂用帳戶種類，以及您是否為新的系統管理員。
- 如果您是新的系統管理員，當您第一次登入訂用帳戶系統管理入口網站時，我們會檢查您具有使用者存取權管理員許可權的 Azure 訂用帳戶。  如果我們找到您的每月訂閱，我們會自動新增這些訂用帳戶。 
- 如果您先前已新增或管理每月訂用帳戶，我們會在每次您登入時檢查新的每月訂閱。 
- 如果您已經是透過大量授權取得的訂用帳戶的系統管理員，但先前尚未新增或管理每月訂閱，您必須使用以下提供的步驟來新增這些訂閱。

## <a name="how-to-add-monthly-subscriptions"></a>如何新增每月訂閱
1. 登入訂用帳戶管理入口網站，網址為<https://manage.visualstudio.com>
1. 在 [**管理訂閱者**] 索引標籤上，選擇 [**新增合約**] 下拉式 
1. 在下拉式選單中選擇 [**新增每月訂閱**]
   > [!div class="mx-imgBorder"]
   > ![[加入新的每月訂閱] 下拉式](_img/add-monthly-subs/add-subs-drop-down.png)
1. 系統會搜尋您擁有使用者存取系統管理員許可權的任何 Azure 訂用帳戶，並匯入使用這些 Azure 訂用帳戶購買的任何 Visual Studio 訂用帳戶。
1. 如果找不到具有使用者存取系統管理員許可權的 Azure 訂用帳戶，或找不到符合資格的 Azure 訂用帳戶，但找不到任何 Visual Studio 訂用帳戶，您將會收到下列訊息：
   > [!div class="mx-imgBorder"]
   > ![找不到新的每月訂閱](_img/add-monthly-subs/no-subs-found.png)
1. 如果找到新的每月訂閱，您會收到確認訊息
   > [!div class="mx-imgBorder"]
   > ![訂閱已新增確認訊息](_img/add-monthly-subs/subs-added-confirmation.png)

## <a name="things-to-keep-in-mind"></a>要牢記在心的事項
- 加入新的每月訂閱的選項，只有在您第一次購買時才可使用。  新增每月訂閱後，每次您登入入口網站時，我們都會檢查新的訂用帳戶。 
- 當找到新的訂用帳戶時，您可能會看到這些訂閱已指派給訂閱者。  這是因為有其他系統管理員具有 Azure 訂用帳戶的存取權，而且他們已經將新的 Visual Studio 訂閱指派給使用者。  現在您已將它們新增至入口網站，您可以管理這些訂用帳戶。 

## <a name="next-steps"></a>接下來的步驟
既然您已新增訂用帳戶，您就可以將它們指派給使用者。  您可以透過數種方式來執行此動作：
- [個別指派訂閱](assign-license.md)
- [指派訂閱給多個使用者](assign-license-bulk.md)
- [將特定訂閱指派給特定使用者](assign-guid.md)

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)
