---
title: 如何指定 ClickOnce 部署的詳細資訊記錄檔 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e1d2ca7c58d7da85ad67e56eae7713e517a1d2c
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381765"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>How to: Specify verbose log files for ClickOnce deployments (如何：指定 ClickOnce 部署的詳細資訊記錄檔)
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]維護所有部署的活動記錄檔。 這些記錄檔詳述有關安裝、初始化、更新和卸載部署的詳細資料 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 若要增加寫入這些記錄檔的詳細資料 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ，請使用登錄編輯程式（*regedit.exe*）來指定詳細資訊層級。

> [!CAUTION]
> 如果您不正確地使用登錄編輯程式，可能會導致嚴重問題，而需要重新安裝作業系統。 您必須自行負擔使用「登錄編輯程式」的風險。

 下列程式描述如何為目前的使用者指定記錄檔的詳細資訊層級 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 若要減少詳細等級，請移除此登錄值。

### <a name="to-specify-verbose-log-files"></a>若要指定詳細資訊記錄檔

1. 開啟 *Regedit.exe*。

2. 流覽至 [ **HKEY_CURRENT_USER \software\classes\software\microsoft\windows\currentversion\deployment**] 節點。

3. 如有必要，請建立名為的新字串值 `LogVerbosityLevel` 。

4. 將 `LogVerbosityLevel` 值設定為 `1` 。

## <a name="see-also"></a>另請參閱
- [針對 ClickOnce 部署進行疑難排解](../deployment/troubleshooting-clickonce-deployments.md)