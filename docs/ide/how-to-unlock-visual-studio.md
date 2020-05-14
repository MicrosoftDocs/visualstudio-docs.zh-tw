---
title: 延長試用版或更新授權
description: 瞭解如何擴展 Visual Studio 的免費試用版、使用線上訂閱或產品金鑰解鎖 Visual Studio 以及更新陳舊或過期的許可證。
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8e11d77a94c7c1d3d7b038ecea1a6c61646e371f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027571"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>延長試用版或更新授權

您可以評估[視覺工作室專業版或視覺工作室企業版](https://visualstudio.microsoft.com/vs/compare/)30 天的免費試用版。 如果您登錄，可以將試用期延長至 90 天。 （視覺工作室社區免費，沒有試用期。 但是，您必須定期[登錄](signing-in-to-visual-studio.md)，以保持[許可證的最新](#update-a-stale-license)。

要在試用期結束後繼續使用 Visual Studio，請使用[線上訂閱](#use-an-online-subscription)或[產品金鑰](#enter-a-product-key)將其解鎖。

## <a name="use-an-online-subscription"></a>使用線上訂閱

1. 選擇 IDE 右上角的 **"登錄**"按鈕（或轉到 **"檔** > **帳戶設置"** 以打開 **"帳戶設置"** 對話方塊，然後選擇"**登錄**"按鈕）。

1. 輸入 Microsoft 帳戶或工作/學校帳戶的認證。 Visual Studio 會尋找與您帳戶建立關聯的 Visual Studio 訂用帳戶或 Azure DevOps 組織。

> [!IMPORTANT]
> 當您從 [Team Explorer]**** 工具視窗連線到 Azure DevOps 組織時，Visual Studio 會自動尋找相關聯的線上訂用帳戶。 當您連線到 Azure DevOps 組織時，您可以使用 Microsoft 帳戶和公司或學校帳戶進行登入。 如果該使用者帳戶有線上訂閱，Visual Studio 會自動為您解除鎖定 IDE。

有關 Visual Studio 訂閱及其工作方式的詳細資訊，請參閱[訂閱支援常見問題頁面](https://visualstudio.microsoft.com/subscriptions/support/)。

## <a name="enter-a-product-key"></a>輸入產品金鑰

1. 選擇 **"檔** > **帳戶設置"** 以打開 **"帳戶設置"** 對話方塊，然後選擇 **"具有產品金鑰"連結的許可證**。

1. 在提供的空格中輸入產品金鑰。

> [!TIP]
> Visual Studio 發行前版本沒有產品金鑰。 您必須登入 IDE 才能使用發行前版本。

有關 Visual Studio 的 Visual Studio 產品金鑰以及如何獲取它們的詳細資訊，請參閱[Visual Studio 訂閱頁中的"使用產品金鑰](/visualstudio/subscriptions/product-keys)"。

## <a name="update-a-stale-license"></a>更新陳舊的許可證

您可能會在 Visual Studio 中看到一條消息，指出"您的許可證已過時，必須更新。

![Visual Studio 授權過時訊息](../ide/media/vs2017_stale-license.png)

此消息指示雖然您的訂閱可能仍然有效，但 Visual Studio 用於使訂閱保持最新狀態的許可證權杖尚未刷新。 Visual Studio 報告許可證已過時，原因如下：

* 您尚未使用 Visual Studio，或者您長時間未連接到互聯網。
* 您已登出 Visual Studio。

在授權權杖過期之前，Visual Studio 會先顯示一個警告訊息，要求您重新輸入認證。

如果不重新輸入憑據，權杖將開始過時，"**帳戶設置"** 對話方塊會告訴您在權杖過期之前還剩多少天。 權杖過期之後，您必須重新輸入帳戶的認證後，才能繼續使用 Visual Studio。

> [!Important]
> 如果您在限制存取或無法存取網際網路的環境中使用 Visual Studio 很長一段時間，則應使用產品金鑰來解除鎖定 Visual Studio，以避免中斷。

## <a name="update-an-expired-license"></a>更新過期的許可證

如果您的訂閱已過期，並且您不再有權訪問 Visual Studio，則必須續訂訂閱或添加具有訂閱的另一個帳戶。 要查看有關您正在使用的許可證的詳細資訊，請訪問 **"檔** > **帳戶設置"** 並查看對話方塊右側的許可證資訊。 如果您有另一個訂閱與其他帳戶關聯，則通過選擇"**添加帳戶"** 連結將該帳戶添加到對話方塊左側的 **"所有帳戶**"清單中。

## <a name="get-support"></a>取得支援

有時會發生一些問題。 如果您遇到問題，以下是一些支援選項：

* 使用["報告問題"](how-to-report-a-problem-with-visual-studio.md)工具報告產品問題。
* 在[訂閱支援常見問題 中](https://visualstudio.microsoft.com/subscriptions/support/)查找有關訂閱、帳戶和計費問題的答案。

## <a name="see-also"></a>另請參閱

* [登入 Visual Studio](../ide/signing-in-to-visual-studio.md)
* [比較視覺工作室版本](https://visualstudio.microsoft.com/vs/compare/)
* [瞭解有關視覺化工作室訂閱的更多](/visualstudio/subscriptions/)
