---
title: 作法：解除鎖定 Visual Studio
titleSuffix: ''
ms.date: 03/30/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: fe0aa86be242e9a7e7ed8d877944c66247718167
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926295"
---
# <a name="how-to-unlock-visual-studio"></a>作法：解除鎖定 Visual Studio

您最多可以免費評估 Visual Studio 30 天。 登入整合式開發環境 (IDE) 可將試用期延展為 90 天。 若要繼續使用 Visual Studio，請透過下列方式之一解除鎖定 IDE：

- 使用線上訂閱

- 輸入產品金鑰

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>使用線上訂閱解除鎖定 Visual Studio

使用與 Microsoft 帳戶、公司或學校帳戶建立關聯的 Visual Studio 訂用帳戶或 Azure DevOps 組織來解除鎖定 Visual Studio：

1. 選擇 IDE 右上角的 [登入]  按鈕 (或移至 [檔案]   > [帳戶設定]  開啟 [帳戶設定]  對話方塊，然後選擇 [登入]  按鈕)。

1. 輸入 Microsoft 帳戶或工作/學校帳戶的認證。 Visual Studio 會尋找與您帳戶建立關聯的 Visual Studio 訂用帳戶或 Azure DevOps 組織。

> [!IMPORTANT]
> 當您從 [Team Explorer]  工具視窗連線到 Azure DevOps 組織時，Visual Studio 會自動尋找相關聯的線上訂用帳戶。 當您連線到 Azure DevOps 組織時，您可以使用 Microsoft 帳戶和公司或學校帳戶進行登入。 如果該使用者帳戶有線上訂閱，Visual Studio 會自動為您解除鎖定 IDE。

## <a name="to-unlock-visual-studio-with-a-product-key"></a>使用產品金鑰解除鎖定 Visual Studio

1. 選取 [檔案]   > [帳戶設定]  開啟 [帳戶設定]  對話方塊，然後選擇 [使用產品金鑰授權]  連結。

1. 在提供的空格中輸入產品金鑰。

> [!TIP]
> Visual Studio 發行前版本沒有產品金鑰。 您必須登入 IDE 才能使用發行前版本。

## <a name="address-license-problem-states"></a>解決授權問題狀態

### <a name="update-stale-licenses"></a>更新過時的授權

您可能會看到下列訊息，指出您的 Visual Studio 授權即將過時。 該訊息為「您的授權已過時，必須更新。」

![Visual Studio 授權過時訊息](../ide/media/vs2017_stale-license.png)

這個訊息表示，雖然您的訂閱可能仍然有效，但是基於下列其中一個原因尚未重新整理 Visual Studio 用來保持最新訂閱的授權權杖，而且該權杖已經過時：

- 您尚未使用 Visual Studio，或有很長一段時間沒有網際網路連線。
- 您已登出 Visual Studio。

在授權權杖過期之前，Visual Studio 會先顯示一個警告訊息，要求您重新輸入認證。

如果您未重新輸入認證，權杖將會過時，且 [帳戶設定]  對話方塊會顯示權杖完全過期之前的天數。 權杖過期之後，您必須重新輸入帳戶的認證後，才能繼續使用 Visual Studio。

> [!Important]
> 如果您在限制存取或無法存取網際網路的環境中使用 Visual Studio 很長一段時間，則應使用產品金鑰來解除鎖定 Visual Studio，以避免中斷。

### <a name="update-expired-licenses"></a>更新到期的授權

如果您的訂用帳戶完全到期，而不再具有 Visual Studio 的存取權限，則必須更新您的訂用帳戶，或新增另一個具有訂用帳戶的帳戶。 若要查看您正在使用之授權的詳細資訊，請移至 [檔案]   > [帳戶設定]  ，並查看對話方塊右側的授權資訊。 如果您有與不同帳戶建立關聯的其他訂閱，請選取 [新增帳戶]  連結，將該帳戶新增到對話方塊左側的 [所有帳戶]  清單。

## <a name="see-also"></a>另請參閱

* [登入 Visual Studio](../ide/signing-in-to-visual-studio.md)
