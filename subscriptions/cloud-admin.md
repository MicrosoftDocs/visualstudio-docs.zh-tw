---
title: 設定雲端訂用帳戶的系統管理員 | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: lank
ms.date: 07/17/2019
ms.topic: conceptual
description: 設定雲端訂用帳戶的系統管理員
ms.openlocfilehash: 62a350e6061444e3c75878dfd89739011c4641d5
ms.sourcegitcommit: 57866dd72fd0e15ce61128df70729b427a2d02eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315211"
---
# <a name="set-up-administrators-for-visual-studio-cloud-subscriptions"></a>設定 Visual Studio 雲端訂用帳戶的系統管理員

Visual Studio 雲端訂用帳戶是由系統管理員管理。 這些人可以指派訂用帳戶、編輯指派、新增或刪除訂用帳戶，以及執行其他訂用帳戶管理工作。

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>Azure 訂用帳戶擁有者是第一個系統管理員

購買 Visual Studio 雲端訂用帳戶時，因為您擁有用來進行購買的 Azure 訂用帳戶，因此會自動將您設定為這些訂用帳戶的系統管理員。

您可以透過 [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) 或者連絡雲端解決方案提供者，來購買雲端訂用帳戶。 如果您透過 Visual Studio Marketplace 進行購買，購買體驗的結尾將提供您管理使用者的機會。 選擇該選項會帶您前往 Visual Studio 訂用帳戶系統管理入口網站 - [https://manage.visualstudio.com](https://manage.visualstudio.com)。

一旦您購買了訂用帳戶，就可以隨時瀏覽[系統管理入口網站](https://manage.visualstudio.com)。 只要登入入口網站，並在左上角選取適當的 Azure 訂用帳戶。

您是 Azure 訂用帳戶的擁有者，並使用此訂用帳戶來購買雲端訂用帳戶，因此您也可以指派額外的系統管理員。

## <a name="add-administrators"></a>新增系統管理員

增系統管理員：

1. 連線到 Azure 入口網站：[portal.azure.com](https://portal.azure.com)。
2. 使用您用來購買 Visual Studio 雲端訂用帳戶的帳戶登入。
3. 在左側瀏覽窗格中，向下捲動至 [成本管理 + 計費]  。
4. 在 [我的訂閱]  清單中，選擇您用來進行購買的 Azure 訂用帳戶。
5. 按一下 [存取控制]  ，它位在左側瀏覽窗格中的清單頂端附近。
6. 按一下頁面頂端的 [新增]  索引標籤。
7. 按一下 [新增角色指派]  。
8. 在右側的飛出窗格中，按一下窗格頂端的 [角色]  下拉式清單，向下捲動並選取 [使用者存取系統管理員]  。
9. 在使用者清單中，向下捲動至您想要設為系統管理員的使用者，並加以選取。 
10. 按一下 [檔案]  。
11. 按一下 [角色指派]  索引標籤，確認您選取的使用者現在會顯示為 [使用者存取系統管理員]。

新的系統管理員現在可以登入[系統管理入口網站](https://manage.visualstudio.com)、從頁面左上角清單中選取與用來購買雲端訂用帳戶相同的 Azure 訂用帳戶，並開始管理那些訂用帳戶。

> [!NOTE]
> 若您看到有存取權可編輯您未在其中被建立為系統管理員之雲端訂用帳戶的使用者，他們在底層 Azure 訂用帳戶中可能擁有可讓他們管理訂用帳戶的 角色。 那些角色包括：擁有者、參與者、服務系統管理員或共同系統管理員。如需詳細資訊，請瀏覽[新增帳單管理員](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts)。

如需 Visual Studio 雲端訂用帳戶的資訊，請參閱＜購買訂用帳戶＞底下的[概觀](vscloud-overview.md)。 若要購買 Visual Studio 雲端訂用帳戶，請瀏覽 Visual Studio Marketplace，網址是 [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription)。
