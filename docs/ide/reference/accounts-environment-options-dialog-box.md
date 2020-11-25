---
title: 帳戶選項參考
description: 瞭解如何設定當您登入 Visual Studio 時，所使用的帳戶相關的一些選項。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cd9f08cb1358d788db661871f6d229d0579ddbd
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871141"
---
# <a name="accounts-environment-options-dialog-box"></a>選項對話方塊、環境、帳戶

使用此頁面來設定與您用來登入 Visual Studio 帳戶的各種相關選項。

## <a name="personalization-account"></a>個人化帳戶

### <a name="synchronize-settings-across-devices"></a>跨裝置同步處理設定

您可以使用此選項，指定是否要在多部電腦之間同步處理您的設定。 如需詳細資訊，請參閱[同步設定](../../ide/synchronized-settings-in-visual-studio.md)。

### <a name="enable-device-code-flow"></a>啟用裝置程式碼流程

選取此選項時，當您選取 [檔案] > [帳戶設定] 頁面的 [新增帳戶]，Visual Studio 的行為會變更。 您並不會看到 [登入您的帳戶] 頁面，而是出現對話方塊，其提供您 URL 和程式碼以貼入至網頁來登入。 若無法以正常方式登入 Visual Studio，例如使用較舊版本的 Internet Explorer 或防火牆限制存取時，此選項十分有用。 如需詳細資訊，請參閱 [Work with multiple user accounts](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow)。

## <a name="registered-azure-clouds"></a>已註冊的 Azure 雲端

本節說明可讓您透過一或多個用來登入 Visual Studio 帳戶存取的 Azure 雲端執行個體。 例如，您可能擁有貴公司資料中心的 Azure 私人執行個體存取權。 或者，您可以存取主權或政府的 Azure 實例，例如 Azure 中國 21 Vianet 或 Azure 美國政府。 根據預設，全域 Azure 雲端執行個體會出現在清單中且無法移除。

選擇 [新增] 按鈕，註冊額外的 Azure 雲端。 [新增 Azure 雲端] 對話方塊會列出數個您可以連線的已知 Azure 雲端執行個體，或者您也可以將 URL 輸入至私人 Azure 端點。

![新增 Azure 雲端執行個體](media/add-new-azure-cloud.png)

註冊額外的 Azure 雲端後，您可以在登入 Visual Studio 時選擇希望登入的 Azure 雲端。

## <a name="see-also"></a>另請參閱

- [跨多部電腦同步處理設定](../synchronized-settings-in-visual-studio.md)
- [登入 Visual Studio](../signing-in-to-visual-studio.md)
- [Work with multiple user accounts](../work-with-multiple-user-accounts.md)
- [環境設定](../environment-settings.md)
