---
title: 測試區域 2： 從原始檔控制取得 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27f2a535b2e08d3632dfd46031823919477fca3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133241"
---
# <a name="test-area-2-get-from-source-control"></a>從原始檔控制取得測試區域 2:
這個測試區域涵蓋測試案例從透過 Get 命令的版本存放區中擷取項目。 這兩個本機和 Web 專案，可以套用這些測試案例。  
  
## <a name="command-menu-access"></a>命令功能表存取  
 下列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]測試案例中使用整合式的開發環境功能表路徑。  
  
##### <a name="get-latest-version"></a>取得最新版本：  
  
-   **檔案**，**原始檔控制**，**取得最新版本**。  
  
-   **檔案**，**取得最新版本**。  
  
-   快顯功能表**取得最新版本**。  
  
-   Get:**檔案**，**原始檔控制**，**取得**。  
  
## <a name="expected-behavior"></a>預期的行為  
  
##### <a name="get-latest-version"></a>取得最新版本：  
 執行無訊息模式中 (沒有 UI) 擷取項目的最新版本從版本儲存區。  
  
##### <a name="get"></a>取得：  
 顯示**取得** 對話方塊，並允許使用者變更的檔案組，將會擷取與修改會影響如何擷取檔案的選項。  
  
## <a name="test-cases"></a>測試案例  
  
|動作|測試步驟|若要確認預期的結果|  
|------------|----------------|--------------------------------|  
|取得最新版本不在本機上的檔案|1.建立專案。<br />2.將項目加入專案。<br />3.將放在原始檔控制專案。<br />4.刪除項目的本機複本。<br />5.取得最新版本的項目 (快顯功能表**取得最新版本**)。|在本機擷取項目檔案。|  
|取得不在本機上的檔案|1.建立專案。<br />2.將項目加入專案。<br />3.將放在原始檔控制專案。<br />4.刪除項目的本機複本。<br />5.取得項目 (**檔案**，**原始檔控制**，**取得**\<項目 >)。|在本機擷取項目檔案。|  
|取得以獨佔方式簽出和修改本機檔案|1.建立專案。<br />2.將項目加入專案。<br />3.將放在原始檔控制專案。<br />4.以獨佔方式簽出專案項目。<br />5.修改本機複本。<br />6.取得最新版本的項目 (**檔案**，**取得最新版本**\<項目 >)。 如果這個步驟成功，請繼續下一個步驟。<br />7.按一下**取代**警告對話方塊中的按鈕。|**從步驟 6 reResult** `:`<br /><br /> 警告對話方塊，表示該檔案已簽出。<br /><br /> **ReResult 步驟 7 中：**<br /><br /> 修改本機檔案取代原始的版本從版本儲存區。<br /><br /> 讀取/寫入檔案。|  
|取得並取代檔案的簽出、 共用，且在本機修改|1.建立新的專案。<br />2.將項目加入專案。<br />3.將放在原始檔控制專案。<br />4.簽出共用的專案項目。<br />5.修改本機複本。<br />6.取得最新版本的項目 (**檔案**，**取得最新版本**\<項目 >)。 如果這個步驟成功，請繼續下一個步驟。<br />7.按一下**取代**警告對話方塊中。|**產生從步驟 6:**<br /><br /> 警告對話方塊，表示該檔案已簽出。<br /><br /> **步驟 7 中產生：**<br /><br /> 修改本機檔案取代原始的版本從版本儲存區。<br /><br /> 讀取/寫入檔案。|  
|取得檔案在本機，存在相同的版本存放區中的最新版本|1.建立新的專案。<br />2.將項目加入專案。<br />3.將放在原始檔控制專案。<br />4.取得項目 (**檔案**，**原始檔控制**，**取得**\<項目 >)。|本機檔案不會變更。|  
|取得具有一個專案的方案|1.建立方案與專案。<br />2.將原始檔控制下的方案。<br />3.刪除所有專案檔在本機。<br />4.取得方案 (**檔案**，**原始檔控制**，**取得**)。|所有已刪除的檔案會在本機上還原。|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)