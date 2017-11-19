---
title: "測試區域 8： 外掛程式切換 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03e7bd5728320bb2efd0b90728b6c1a16f5997ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-8-plug-in-switching"></a>測試區域 8： 外掛程式切換
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 具有使用者介面 (UI)，若要變更目前的原始檔控制外掛程式。 這個測試區域會提供挑選的外掛程式用於原始檔控制方案的程序中的測試案例。  
  
## <a name="command-menu-access"></a>命令功能表存取  
 下列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]測試案例中使用整合式的開發環境功能表路徑。  
  
-   目前的原始檔控制外掛程式：**工具** -> **選項** -> **原始檔控制** -> **外掛程式選取範圍**.  
  
-   變更原始檔控制繫結：**檔案** -> **原始檔控制** -> **變更原始檔控制**...  
  
## <a name="common-expected-behavior"></a>常見的預期的行為  
 變更原始檔控制外掛程式的解決方案是可能不需要結束 Visual Studio，或重新載入解決方案。 此外，目前的原始檔控制外掛程式會自動變更該方案載入時所用的方案。  
  
## <a name="test-cases"></a>測試案例  
 以下是用於外掛程式的切換測試區域的特定測試案例。  
  
### <a name="case-8a-automatic-change"></a>大小寫 8a： 自動變更  
  
#### <a name="expected-behavior"></a>預期的行為  
 當使用者載入原始檔控制下的解決方案時，方案就會自動載入，並為目前選取適當的原始檔控制外掛程式。  
  
|動作|測試步驟|若要確認預期的結果|  
|------------|----------------|--------------------------------|  
|自動的原始檔控制外掛程式變更|1.選取外掛程式在測試為目前 (**工具** -> **選項** -> **原始檔控制** -> **外掛程式選取項目**。)<br />2.建立新的專案。<br />3.將方案加入原始檔控制。<br />4.選取另一個外掛程式 (例如， [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])。<br />5.接受卸載方案提示字元。<br />6.重新開啟方案，從磁碟。|開啟的方案。<br /><br /> 測試外掛程式是目前的原始檔控制外掛程式。|  
  
### <a name="case-8b-solution-based-change"></a>大小寫 8b： 方案架構的變更  
  
#### <a name="expected-behavior"></a>預期的行為  
 方案可以有與其關聯的原始檔控制外掛程式變更。  
  
|動作|測試步驟|若要確認預期的結果|  
|------------|----------------|--------------------------------|  
|外掛程式之方案的變更|1.選取外掛程式在測試為目前 (**工具** -> **選項** -> **原始檔控制** -> **外掛程式選取項目**)。<br />2.建立新的專案和方案。<br />3.將方案加入原始檔控制。<br />4.從原始檔控制方案解除繫結 (使用**變更原始檔控制**對話方塊)。<br />5.選取另一個外掛程式 (例如， [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])。<br />6.如果已卸載，請重新載入解決方案從磁碟。<br />7.將方案加入原始檔控制。<br />8.從原始檔控制方案解除繫結 (使用**變更原始檔控制**對話方塊)。<br />9.選取 下一次測試外掛程式。<br />10.如果卸載，請重新載入解決方案的磁碟。<br />11.將方案繫結至原始位置 (使用**變更原始檔控制**對話方塊)。|使用所選方案加入至原始檔控制外掛程式。|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)