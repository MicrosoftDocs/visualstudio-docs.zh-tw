---
title: 測試區域 2： 取得從原始檔控制 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d30b4a246085fe3a1339e057e516a9a727af1cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496550"
---
# <a name="test-area-2-get-from-source-control"></a>測試區域 2︰從原始檔控制中取得
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[測試區域 2： 從原始檔控制取得](https://docs.microsoft.com/visualstudio/extensibility/internals/test-area-2-get-from-source-control)。  
  
此測試區域涵蓋測試案例，透過 Get 命令的版本存放區擷取項目。 這些測試案例可以套用至這兩個本機和 Web 專案。  
  
## <a name="command-menu-access"></a>命令功能表存取  
 下列[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]與測試案例中使用整合式的開發環境功能表路徑。  
  
##### <a name="get-latest-version"></a>取得最新版本：  
  
-   **檔案**，**原始檔控制**，**取得最新版本**。  
  
-   **檔案**，**取得最新版本**。  
  
-   快顯功能表**取得最新版本**。  
  
-   Get:**檔案**，**原始檔控制**，**取得**。  
  
## <a name="expected-behavior"></a>預期的行為  
  
##### <a name="get-latest-version"></a>取得最新版本：  
 執行無訊息模式 (無 UI) 擷取之項目的最新版本的版本存放區。  
  
##### <a name="get"></a>取得此項目：  
 顯示**取得** 對話方塊中，並可讓使用者進行變更的檔案集合將會擷取，以及修改會影響如何擷取檔案的選項。  
  
## <a name="test-cases"></a>測試案例  
  
|動作|測試步驟|若要確認預期的結果|  
|------------|----------------|--------------------------------|  
|取得最新版本不在本機上的檔案|1.建立專案。<br />2.將項目加入至專案。<br />3.將放在原始檔控制專案。<br />4.刪除項目的本機副本。<br />5.取得最新版本的項目 (快顯功能表**取得最新版本**)。|在本機擷取項目檔案。|  
|取得不在本機上的檔案|1.建立專案。<br />2.將項目加入至專案。<br />3.將放在原始檔控制專案。<br />4.刪除項目的本機副本。<br />5.取得項目 (**檔案**，**原始檔控制**，**取得**\<項目 >)。|在本機擷取項目檔案。|  
|取得以獨佔方式簽出和修改在本機的檔案|1.建立專案。<br />2.將項目加入至專案。<br />3.將放在原始檔控制專案。<br />4.以獨佔方式簽出專案項目。<br />5.修改本機複本。<br />6.取得最新版本的項目 (**檔案**，**取得最新版**\<項目 >)。 如果這個步驟成功，則會繼續至下一個步驟。<br />7.按一下 **取代**警告 對話方塊中的按鈕。|**步驟 6 reResult** `:`<br /><br /> 警告 對話方塊中指出該檔案已簽出。<br /><br /> **ReResult 的步驟 7:**<br /><br /> 修改本機檔案會取代原始版本的版本存放區。<br /><br /> 讀取/寫入檔案。|  
|取得並取代檔案的簽出、 共用，且在本機修改|1.建立新的專案。<br />2.將項目加入至專案。<br />3.將放在原始檔控制專案。<br />4.請查看為共用的專案項目。<br />5.修改本機複本。<br />6.取得最新版本的項目 (**檔案**，**取得最新版**\<項目 >)。 如果這個步驟成功，則會繼續至下一個步驟。<br />7.按一下 **取代**在警告對話方塊中。|**產生從步驟 6:**<br /><br /> 警告 對話方塊中指出該檔案已簽出。<br /><br /> **產生的步驟 7:**<br /><br /> 修改本機檔案會取代原始版本的版本存放區。<br /><br /> 讀取/寫入檔案。|  
|取得的檔案，並在本機，存在相同的版本存放區中的最新版本|1.建立新的專案。<br />2.將項目加入至專案。<br />3.將放在原始檔控制專案。<br />4.取得項目 (**檔案**，**原始檔控制**，**取得**\<項目 >)。|本機檔案不會變更。|  
|取得具有一個專案的方案|1.使用一個專案中建立方案。<br />2.將放在原始檔控制解決方案。<br />3.刪除所有的專案檔在本機。<br />4.取得方案 (**檔案**，**原始檔控制**，**取得**)。|所有已刪除的檔案會在本機上還原。|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

