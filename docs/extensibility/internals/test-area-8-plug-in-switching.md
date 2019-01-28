---
title: 測試區域 8︰外掛程式切換 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 460d3afc18c19b7e7e3ed97725d69b5a8b04a382
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998660"
---
# <a name="test-area-8-plug-in-switching"></a>測試區域 8︰外掛程式切換
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 有使用者介面 (UI) 來變更目前的原始檔控制外掛程式。 此測試區域會提供挑選的外掛程式用於原始檔控制方案的程序中的測試案例。  

## <a name="command-menu-access"></a>命令功能表存取  
 下列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]與測試案例中使用整合式的開發環境功能表路徑。  

-   目前的原始檔控制外掛程式：**工具** -> **選項** -> **原始檔控制** -> **外掛程式選擇**。  

-   變更原始檔控制繫結：**檔案** -> **原始檔控制** -> **變更原始檔控制**...  

## <a name="common-expected-behavior"></a>常見的預期的行為  
 變更原始檔控制外掛程式的解決方案是可能不需要結束 Visual Studio，或重新載入方案。 此外，目前的原始檔控制外掛程式會自動變更為該方案載入時，解決方案所用的一個。  

## <a name="test-cases"></a>測試案例  
 以下是外掛程式切換的測試區域的特定測試案例。  

### <a name="case-8a-automatic-change"></a>案例 8a:自動變更  

#### <a name="expected-behavior"></a>預期的行為  
 當使用者載入原始檔控制下的解決方案時，自動載入方案時，為目前選取適當的原始檔控制外掛程式。  


| 動作 | 測試步驟 | 若要確認預期的結果 |
| - | - | - |
| 自動的原始檔控制外掛程式的變更 | 1.選取外掛程式下測試一樣新 (**工具** -> **選項** -> **原始檔控制** -> **外掛程式選取項目**。)<br />2.建立新的專案。<br />3.您可以將方案加入原始檔控制。<br />4.選取另一個外掛程式 (例如[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])。<br />5.接受卸載方案提示。<br />6.重新開啟方案，從磁碟。 | 開啟的方案。<br /><br /> 受測試的外掛程式是目前的原始檔控制外掛程式。 |

### <a name="case-8b-solution-based-change"></a>案例 8b:解決方案為基礎的變更  

#### <a name="expected-behavior"></a>預期的行為  
 方案可以有與其關聯的原始檔控制外掛程式已變更。  


| 動作 | 測試步驟 | 若要確認預期的結果 |
|----------------------------------| - | - |
| 變更的外掛程式的解決方案 | 1.選取外掛程式下測試一樣新 (**工具** -> **選項** -> **原始檔控制** -> **外掛程式選取項目**)。<br />2.建立新的專案和方案。<br />3.您可以將方案加入原始檔控制。<br />4.從原始檔控制方案解除繫結 (使用**變更原始檔控制**對話方塊)。<br />5.選取另一個外掛程式 (例如[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])。<br />6.如果已卸載，請重新載入從磁碟解決方案。<br />7.您可以將方案加入原始檔控制。<br />8.從原始檔控制方案解除繫結 (使用**變更原始檔控制**對話方塊)。<br />9.選取下一次測試外掛程式。<br />10.如果已卸載，請重新載入方案，從磁碟。<br />11.將方案繫結到原始位置 (使用**變更原始檔控制**對話方塊)。 | 使用所選解決方案新增至原始檔控制外掛程式。 |

## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)