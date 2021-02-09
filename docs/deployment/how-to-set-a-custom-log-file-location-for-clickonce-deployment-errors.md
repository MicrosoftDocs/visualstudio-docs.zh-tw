---
title: '設定自訂記錄檔位置 (ClickOnce 部署錯誤) '
description: 瞭解 ClickOnce 針對所有部署所維護的啟用記錄檔，這會記載安裝和初始化 ClickOnce 部署的錯誤。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e527e1aec630faadec6e594f944a6715028c6d82
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885049"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>How to: Set a custom log file location for ClickOnce deployment errors (如何：設定 ClickOnce 部署錯誤的自訂記錄檔位置)
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 維護所有部署的啟用記錄檔。 這些記錄會記錄有關安裝和初始化部署的任何錯誤 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 依預設，會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 為每個部署啟用建立一個記錄檔。 它會將這些記錄檔儲存在 [Temporary Internet Files] 資料夾中。 當啟用失敗時，使用者會看到部署的記錄檔，而使用者會在產生的錯誤對話方塊中按一下 [ **詳細資料** ]。

 您可以使用登錄編輯程式 (**regedit.exe**) 設定自訂的記錄檔路徑，來變更特定用戶端的這個行為。 在此情況下，會 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 針對單一檔案中的所有部署記錄啟用成功和失敗。

> [!CAUTION]
> 如果未正確使用登錄編輯程式，可能會導致嚴重問題，甚至可能必須重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。

> [!NOTE]
> 您必須偶爾截斷或刪除記錄檔，以防止其成長過大。

 下列程式描述如何設定單一用戶端的自訂記錄檔位置。

### <a name="to-set-a-custom-log-file-location"></a>若要設定自訂記錄檔位置

1. 開啟 **Regedit.exe**。

2. 流覽至節點 `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` 。

3. 將字串值設定 `LogFilePath` 為您慣用的自訂記錄檔位置的完整路徑和檔案名。

     這個位置必須位於使用者具有寫入權限的目錄中。 例如，在 Windows Vista 上，建立下列資料夾結構並設定 `LogFilePath` 為 *C:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*。

## <a name="see-also"></a>另請參閱
- [針對 ClickOnce 部署進行疑難排解](../deployment/troubleshooting-clickonce-deployments.md)