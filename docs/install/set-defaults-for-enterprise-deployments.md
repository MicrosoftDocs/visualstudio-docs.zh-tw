---
title: "設定 Visual Studio 企業部署的預設值 | Microsoft Docs"
description: "Visual Studio 企業部署的網域原則和其他設定作業。"
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 11bcc331150b1e1ab9a8058b3538bca411345c19
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>設定 Visual Studio 企業部署的預設值

您可以設定會影響 Visual Studio 部署的登錄原則。 這些原則全面適用於新的安裝程式，而且會影響︰

- 與其他版本或執行個體共用之某些套件安裝的位置
- 快取套件的位置
- 是否快取所有的套件

您可以使用[命令列選項](use-command-line-parameters-to-install-visual-studio.md)設定這些原則中的某些原則、在您的電腦上設定登錄值，或者甚至使用群組原則在整個組織發佈它們。

## <a name="registry-keys"></a>登錄機碼

您可以在數個位置設定企業預設值，以透過群組原則或直接在登錄中啟用其控制。 Visual Studio 會循序查看是否有任何已設定的企業原則，只要一發現下列順序的原則值，則會忽略剩餘的機碼。

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (64 位元作業系統)

> [!IMPORTANT]
> 如果您未設定 `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` 機碼並改為設定其他機碼之一，您應該在 64 位元作業系統上設定其他兩個機碼。 未來產品更新中將解決此問題。

如果尚未設定，某些登錄值會在第一次使用時自動設定。 這種做法可確保後續安裝會使用相同的值。 這些值會儲存在第二個登錄機碼 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` 中。

您可以設定下列登錄值：

| **Name** | **類型** | **預設值** | **描述** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` 或 `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | 儲存套件資訊清單和套件承載 (後者為選擇性) 的目錄。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | 保留套件承載，即使已安裝它們。 您可以隨時變更該值。 停用原則將移除您所修復或修改之執行個體的任何已快取套件承載。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `SharedInstallationPath` | `REG_SZ` 或 `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | 在各個 Visual Studio 執行個體版本上共用之某些套件的安裝目錄。 您可以隨時變更該值，但這只會影響未來的安裝。 任何已安裝在舊位置的產品都不得移動，否則可能無法正常運作。 |

> [!IMPORTANT]
> 如果您在任何安裝之後變更 `CachePath` 登錄原則，則必須將現有的套件快取移動至新的位置並確定它受到保護，讓 `SYSTEM` 和 `Administrators` 兩者具有完全控制權限，而 `Everyone` 具有讀取權限。
> 移動現有快取或提供其保護失敗，可能會造成日後的安裝問題。

## <a name="get-support"></a>取得支援
有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面，以取得疑難排解祕訣。 同樣地，您可以透過 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具向我們報告產品問題，或者在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享建議。 您可以在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)追蹤產品問題，也可以在那裡詢問問題和尋找解答。 您也可以透過我們在 [Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動 (需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>請參閱

 * [安裝 Visual Studio](install-visual-studio.md)
 * [停用或移動套件快取](disable-or-move-the-package-cache.md)
 * [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
