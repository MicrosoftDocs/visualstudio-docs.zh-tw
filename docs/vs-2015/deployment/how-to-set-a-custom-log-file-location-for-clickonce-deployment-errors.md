---
title: 如何：設定 ClickOnce 部署錯誤的自訂記錄檔位置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a1b7c93e4b30bbfd373a5fad9d7001452d4f587
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838894"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>如何：設定 ClickOnce 部署錯誤的自訂記錄檔位置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 維護所有部署的啟用記錄檔。 這些記錄會記錄有關安裝和初始化部署的任何錯誤 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 。 依預設，會 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 為每個部署啟用建立一個記錄檔。 它會將這些記錄檔儲存在 [Temporary Internet Files] 資料夾中。 當啟用失敗時，使用者會看到部署的記錄檔，而使用者會在產生的錯誤對話方塊中按一下 [ **詳細資料** ]。  
  
 您可以使用登錄編輯程式 (**regedit.exe**) 設定自訂的記錄檔路徑，來變更特定用戶端的這個行為。 在此情況下，會 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 針對單一檔案中的所有部署記錄啟用成功和失敗。  
  
> [!CAUTION]
> 如果未正確使用登錄編輯程式，可能會導致嚴重問題，甚至可能必須重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。  
  
> [!NOTE]
> 您必須偶爾截斷或刪除記錄檔，以防止其成長過大。  
  
 下列程式描述如何設定單一用戶端的自訂記錄檔位置。  
  
### <a name="to-set-a-custom-log-file-location"></a>若要設定自訂記錄檔位置  
  
1. 開啟 **Regedit.exe**。  
  
2. 流覽至節點 `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` 。  
  
3. 將字串值設定 `LogFilePath` 為您慣用的自訂記錄檔位置的完整路徑和檔案名。  
  
     這個位置必須位於使用者具有寫入權限的目錄中。 例如，在 Windows Vista 上建立下列資料夾結構，並設定 `LogFilePath` 為 C:\Users \\<username \> \Documents\Logs\ClickOnce\installation.log。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)
