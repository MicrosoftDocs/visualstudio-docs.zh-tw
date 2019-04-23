---
title: HOW TO：指定供 ClickOnce 部署的詳細資訊記錄檔 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e200d0918e3d346f71da6ec2184e07e7d8433174
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069766"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>HOW TO：指定供 ClickOnce 部署使用的詳細資訊記錄檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 會維護所有部署的活動記錄檔。 這些記錄檔記錄有關安裝、 初始化、 更新及解除安裝的詳細資料[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]部署。 若要增加詳細資料，[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]寫入這些記錄檔，使用登錄編輯程式 (**regedit.exe**) 指定的詳細資訊層級。  
  
> [!CAUTION]
>  如果您不當使用登錄編輯程式，您可能會導致嚴重的問題，可能會要求您重新安裝作業系統。 使用登錄編輯程式的風險須自行承擔。  
  
 下列程序描述如何指定詳細等級[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]記錄檔以取得目前的使用者。 若要減少層級的詳細資訊，請移除此登錄值。  
  
### <a name="to-specify-verbose-log-files"></a>若要指定詳細資訊記錄檔  
  
1. 開啟**Regedit.exe**。  
  
2. 瀏覽至節點`HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`。  
  
3. 如有必要，建立名為的新字串值`LogVerbosityLevel`。  
  
4. 設定`LogVerbosityLevel`值`1`。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)
