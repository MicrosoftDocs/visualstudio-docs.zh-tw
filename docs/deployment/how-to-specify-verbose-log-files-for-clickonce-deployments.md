---
title: "如何： 指定 ClickOnce 部署的詳細資訊記錄檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 6cac7764a941e88dd3901a3280e78717955e86b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>如何：指定供 ClickOnce 部署使用的詳細資訊記錄檔
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]會維護所有部署的活動記錄檔。 這些記錄檔記錄有關安裝、 初始化、 更新及解除安裝的詳細資料[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。 若要增加詳細資料，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]寫入這些記錄檔，使用登錄編輯程式 (**regedit.exe**) 來指定詳細等級。  
  
> [!CAUTION]
>  如果您不當使用登錄編輯程式，您可能會導致嚴重的問題，可能需要重新安裝作業系統。 使用登錄編輯程式的風險須自行承擔。  
  
 下列程序描述如何指定詳細等級[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]記錄檔以取得目前的使用者。 若要減少層級的詳細資訊，請移除此登錄值。  
  
### <a name="to-specify-verbose-log-files"></a>若要指定詳細資訊記錄檔  
  
1.  開啟**Regedit.exe**。  
  
2.  巡覽至節點`HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`。  
  
3.  如有必要，建立名為的新字串值`LogVerbosityLevel`。  
  
4.  設定`LogVerbosityLevel`值設定為`1`。  
  
## <a name="see-also"></a>請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)