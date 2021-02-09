---
title: 延長試用版或更新授權
description: 瞭解如何延長 Visual Studio 的免費試用版、使用線上訂用帳戶或產品金鑰來解除鎖定 Visual Studio，以及更新過期或過期的授權。
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 3dd2a688ef70064f44caccfd7c64150b7c649769
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869124"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>延長試用版或更新授權

您可以評估 [Visual Studio Professional 或 Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) 30 天的免費試用。 如果您登入，您可以將試用期間延長至90天。  (Visual Studio Community 免費，沒有試用期。 不過，您必須定期登入，讓您的授權保持[在](signing-in-to-visual-studio.md)[最](#update-a-stale-license)新狀態。 ) 

若要在試用期間結束後繼續使用 Visual Studio，請使用 [線上訂](#use-an-online-subscription) 用帳戶或 [產品金鑰](#enter-a-product-key)將其解除鎖定。

## <a name="use-an-online-subscription"></a>使用線上訂用帳戶

1. 選擇 IDE 右上角的 [登 **入**] 按鈕 (或 **移至 [** 檔案  >  **帳戶設定**] 開啟 [**帳戶設定**] 對話方塊，然後選擇 [登 **入**] 按鈕) 。

1. 輸入 Microsoft 帳戶或工作/學校帳戶的認證。 Visual Studio 會尋找與您帳戶建立關聯的 Visual Studio 訂用帳戶或 Azure DevOps 組織。

> [!IMPORTANT]
> 當您從 [Team Explorer] 工具視窗連線到 Azure DevOps 組織時，Visual Studio 會自動尋找相關聯的線上訂用帳戶。 當您連線到 Azure DevOps 組織時，您可以使用 Microsoft 帳戶和公司或學校帳戶進行登入。 如果該使用者帳戶有線上訂閱，Visual Studio 會自動為您解除鎖定 IDE。

如需 Visual Studio 訂用帳戶和其運作方式的詳細資訊，請參閱 [訂閱支援常見問題](https://visualstudio.microsoft.com/subscriptions/support/) 頁面。

## <a name="enter-a-product-key"></a>輸入產品金鑰

1. 選取 **[** 檔案  >  **帳戶設定**] 以開啟 [**帳戶設定**] 對話方塊，然後選擇 [**具有產品金鑰的授權**] 連結。

1. 在提供的空格中輸入產品金鑰。

> [!TIP]
> Visual Studio 發行前版本沒有產品金鑰。 您必須登入 IDE 才能使用發行前版本。

如需 Visual Studio Visual Studio 產品金鑰的詳細資訊，以及如何取得這些金鑰的詳細資訊，請參閱 [Visual Studio 訂用帳戶中的使用產品金鑰](/visualstudio/subscriptions/product-keys) 頁面。

## <a name="update-a-stale-license"></a>更新過時的授權

您可能會在 Visual Studio 中看到一則訊息，指出「您的授權已過時，必須更新。」

![Visual Studio 授權過時訊息](../ide/media/vs2017_stale-license.png)

這則訊息表示，雖然您的訂閱可能仍然有效，但是 Visual Studio 用來保持訂用帳戶最新狀態的授權權杖尚未重新整理。 Visual Studio 報告因為下列其中一個原因而導致授權過時：

* 您未使用 Visual Studio 或您已有一段很長的時間未連線到網際網路。
* 您已登出 Visual Studio。

在授權權杖過期之前，Visual Studio 會先顯示一個警告訊息，要求您重新輸入認證。

如果您未重新輸入認證，權杖將會開始過時，且 [ **帳戶設定** ] 對話方塊會告知您權杖到期前的剩餘天數。 權杖過期之後，您必須重新輸入帳戶的認證後，才能繼續使用 Visual Studio。

> [!Important]
> 如果您在限制存取或無法存取網際網路的環境中使用 Visual Studio 很長一段時間，則應使用產品金鑰來解除鎖定 Visual Studio，以避免中斷。

## <a name="update-an-expired-license"></a>更新過期的授權

如果您的訂用帳戶已過期，且您不再有 Visual Studio 的存取權限，您必須更新您的訂用帳戶，或新增另一個具有訂用帳戶的帳戶。 若要查看您所使用之授權的詳細資訊，請 **移至 [** 檔案  >  **帳戶設定**]，並查看對話方塊右側的授權資訊。 如果您有另一個與不同帳戶相關聯的訂用帳戶，請選取 [**新增帳戶**] 連結，將該帳戶新增至對話方塊左側的 [**所有帳戶**] 清單。

## <a name="get-support"></a>取得支援

有時會發生一些問題。 如果您遇到問題，以下是一些支援選項：

* 使用「回報 [問題](how-to-report-a-problem-with-visual-studio.md) 」工具來報告產品問題。
* 在訂用帳戶 [支援常見問題](https://visualstudio.microsoft.com/subscriptions/support/)中尋找訂用帳戶、帳戶及帳單相關問題的解答。

## <a name="see-also"></a>另請參閱

* [登入 Visual Studio](../ide/signing-in-to-visual-studio.md)
* [比較 Visual Studio 版本](https://visualstudio.microsoft.com/vs/compare/)
* [深入瞭解 Visual Studio 訂閱](/visualstudio/subscriptions/)
