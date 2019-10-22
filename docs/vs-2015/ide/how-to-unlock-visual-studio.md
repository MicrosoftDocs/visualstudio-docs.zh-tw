---
title: 解除鎖定 Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a71a045661c48fd36733ecd8d2266470667a5c35
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670600"
---
# <a name="how-to-unlock-visual-studio"></a>如何解除鎖定 Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您最多可以免費評估 Visual Studio 30 天。 當您登入 IDE 時，您可以將試用期延長 90 天。 若要繼續使用 Visual Studio，您可以透過下列方式解除鎖定 IDE：

1. 使用線上訂閱。

2. 輸入產品金鑰。

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>使用線上訂閱解除鎖定 Visual Studio
 若要使用與 Microsoft 帳戶或工作/學校帳戶關聯的 MSDN 訂閱或 Visual Studio Online 訂閱解除鎖定 Visual Studio：

1. 按一下 IDE 右上角的 [登入] 按鈕 (或移至 [檔案] > [帳戶設定] 開啟 [帳戶設定] 對話方塊，然後按一下 [登入] 按鈕)。

2. 輸入 Microsoft 帳戶或工作/學校帳戶的認證。 Visual Studio 將會尋找與您的帳戶關聯的 MSDN 訂閱或 Visual Studio Team Services 訂閱。

> [!IMPORTANT]
> 當您從 Team Explorer 工具視窗連線到 Visual Studio Team Services 帳戶時，Visual Studio 會自動尋找關聯的線上訂閱。 當您連線到 Visual Studio Team Services 帳戶時，您可以使用 Microsoft 帳戶和工作/學校帳戶進行登入。 如果該使用者帳戶有線上訂閱，Visual Studio 會自動為您解除鎖定 IDE。

## <a name="to-unlock-visual-studio-with-a-product-key"></a>使用產品金鑰解除鎖定 Visual Studio

1. 選取 [檔案] > [帳戶設定]  開啟 [帳戶設定] 對話方塊，然後按一下 [使用產品金鑰授權]  連結。

2. 在提供的空格中輸入產品金鑰。

> [!TIP]
> Visual Studio 發行前版本不需要產品金鑰。 您必須登入 IDE 才能使用發行前版本。

## <a name="addressing-license-problem-states"></a>解決授權問題狀態

### <a name="updating-stale-licenses"></a>更新過時的授權
 您可能會看到下列訊息，顯示您的 Visual Studio 授權即將過時。

 ![Visual Studio [使用者資訊] 對話方塊](../ide/media/vs2013-userinfo.png "|::ref1::|")

 這個訊息表示，雖然您的訂閱可能仍然有效，但是基於下列其中一個原因尚未重新整理 Visual Studio 用來保持最新訂閱的授權權杖，而且該權杖已經過時：

1. 您尚未使用 Visual Studio，或有很長一段時間沒有網際網路連線。

2. 您已登出 Visual Studio。

   在授權權杖過期之前，Visual Studio 會先顯示一個警告訊息，要求您重新輸入認證。

   如果您未重新輸入認證，則權杖會開始過時。 當發生這種情況時，[帳戶設定] 對話方塊會通知您在權杖完全過期之前還剩下多少天。 權杖過期之後，您必須使用上述另一個方法重新輸入這個帳戶或授權的認證，才能繼續使用 Visual Studio。

> [!IMPORTANT]
> 如果您在限制存取或無法存取網際網路的環境中使用 Visual Studio 很長一段時間，則應使用產品金鑰來解除鎖定 Visual Studio，以避免中斷。

### <a name="updating-expired-licenses"></a>更新到期的授權
 如果您的訂閱完全到期，而不再具有 Visual Studio 的存取權限，您必須：

1. 更新您的訂閱 若要查看您正在使用之授權的詳細資訊，請移至 [檔案] > [帳戶設定] 對話方塊，並查看對話方塊右側的授權資訊。

2. 如果您有與不同帳戶關聯的另一個訂閱，請按一下 [加入帳戶…] 連結，將該帳戶加入 [檔案] > [帳戶設定] 對話方塊左側的 [所有帳戶] 清單中。

## <a name="see-also"></a>另請參閱
 [登入 Visual Studio](../ide/signing-in-to-visual-studio.md)
