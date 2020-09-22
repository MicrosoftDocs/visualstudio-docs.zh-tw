---
title: 如何：指定 ClickOnce 部署的詳細資訊記錄檔 |Microsoft Docs
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
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839216"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>如何：指定供 ClickOnce 部署使用的詳細資訊記錄檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 維護所有部署的活動記錄檔。 這些記錄會記錄有關安裝、初始化、更新及卸載部署的詳細資料 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 。 若要增加寫入這些記錄檔的詳細資料 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ，請使用登錄編輯程式 (**regedit.exe**) 來指定詳細等級。  
  
> [!CAUTION]
> 如果您不正確地使用登錄編輯程式，可能會導致嚴重問題，而需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。  
  
 下列程式描述如何為目前使用者指定記錄檔的詳細資訊層級 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 。 若要減少詳細程度，請移除此登錄值。  
  
### <a name="to-specify-verbose-log-files"></a>指定詳細資訊記錄檔  
  
1. 開啟 **Regedit.exe**。  
  
2. 流覽至節點 `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` 。  
  
3. 如有必要，請建立名為的新字串值 `LogVerbosityLevel` 。  
  
4. 將 `LogVerbosityLevel` 值設定為 `1` 。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 ClickOnce 部署](../deployment/troubleshooting-clickonce-deployments.md)
