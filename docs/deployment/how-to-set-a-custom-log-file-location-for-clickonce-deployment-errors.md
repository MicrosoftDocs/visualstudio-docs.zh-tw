---
title: 如何： 設定 ClickOnce 部署錯誤的自訂記錄檔位置 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab6d1e1fe21d8da667963f9b54db23f303e6aee7
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079170"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>如何： 設定 ClickOnce 部署錯誤的自訂記錄檔位置
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 會維護所有部署的啟動記錄檔。 這些記錄檔記錄有關安裝和初始化任何錯誤[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。 根據預設，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]建立每個部署啟動的一個記錄檔。 它會這些記錄檔儲存在 Temporary Internet Files 資料夾中。 部署記錄檔顯示給使用者時啟用失敗，且使用者按下**詳細資料**在產生的 [錯誤] 對話方塊。  
  
 您也可以使用登錄編輯程式特定的用戶端變更此行為 (**regedit.exe**) 來設定自訂的記錄檔路徑。 在此情況下，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]記錄啟用成功與失敗之所有部署在單一檔案。  
  
> [!CAUTION]
>  如果您不當使用登錄編輯程式，您可能會導致嚴重的問題，可能會要求您重新安裝作業系統。 使用登錄編輯程式的風險須自行承擔。  
  
> [!NOTE]
>  您必須截斷或刪除記錄檔，偶爾會以防止它變得太大。  
  
 下列程序描述如何設定單一用戶端的自訂記錄檔的位置。  
  
### <a name="to-set-a-custom-log-file-location"></a>若要設定的自訂記錄檔位置  
  
1.  開啟**Regedit.exe**。  
  
2.  瀏覽至節點`HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`。  
  
3.  設定字串值`LogFilePath`完整路徑和檔名的您慣用的自訂記錄檔的位置。  
  
     此位置必須是使用者具有寫入權限的目錄中。 例如，在 Windows Vista 中，建立下列資料夾結構，並設定`LogFilePath`要*C:\Users\\\<使用者名稱 > \Documents\Logs\ClickOnce\installation.log*。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)