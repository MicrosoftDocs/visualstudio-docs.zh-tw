---
title: 測試區域8：外掛程式切換 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb815a773351c1bb6212962a639e2758114a0e2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722424"
---
# <a name="test-area-8-plug-in-switching"></a>測試區域 8︰外掛程式切換
@No__t_0 的整合式開發環境（IDE）有使用者介面（UI），可變更目前的原始檔控制外掛程式。 這個測試區域會提供測試案例，供您挑選要用於解決方案原始檔控制的外掛程式。

## <a name="command-menu-access"></a>命令功能表存取
 下列 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的整合式開發環境功能表路徑用於測試案例中。

- 目前的原始檔控制外掛程式： [**工具**]  -> **選項** -> **原始檔控制** -> **外掛程式選取範圍**。

- 變更原始檔控制系結：**檔案  -> ** **原始檔控制** -> **變更原始檔控制**。

## <a name="common-expected-behavior"></a>常見的預期行為
 不需要結束 Visual Studio 或重載解決方案，即可變更解決方案的原始檔控制外掛程式。 此外，當載入方案時，目前的原始檔控制外掛程式會自動變更為方案所使用的外掛程式。

## <a name="test-cases"></a>測試案例
 以下是外掛程式切換測試區域的特定測試案例。

### <a name="case-8a-automatic-change"></a>案例8a：自動變更

#### <a name="expected-behavior"></a>預期的行為
 當使用者載入位於原始檔控制之下的方案時，會自動載入方案，並選取適當的原始檔控制外掛程式做為目前的。

| 動作 | 測試步驟 | 要驗證的預期結果 |
| - | - | - |
| 自動原始檔控制外掛程式變更 | 1. 將 [測試] 底下的 [外掛程式] 選取為 [目前] （[**工具**]  -> **選項** -> **原始檔控制** -> **外掛程式選取範圍**）。<br />2. 建立新的專案。<br />3. 將方案加入至原始檔控制。<br />4. 選取另一個外掛程式（例如，[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]）。<br />5. 接受卸載解決方案提示。<br />6. 從磁片重新開啟解決方案。 | 方案已開啟。<br /><br /> [測試中] 外掛程式是目前的原始檔控制外掛程式。 |

### <a name="case-8b-solution-based-change"></a>案例8b：以解決方案為基礎的變更

#### <a name="expected-behavior"></a>預期的行為
 方案可以變更其相關聯的原始檔控制外掛程式。

| 動作 | 測試步驟 | 要驗證的預期結果 |
|----------------------------------| - | - |
| 解決方案的外掛程式變更 | 1. 將 [測試] 底下的 [外掛程式] 選取為 [目前] （[**工具**]  -> **選項** -> **原始檔控制** -> **外掛程式選取範圍**）。<br />2. 建立新的專案和方案。<br />3. 將方案加入至原始檔控制。<br />4. 從原始檔控制解除方案的系結（使用 [**變更原始檔控制**] 對話方塊）。<br />5. 選取另一個外掛程式（例如，[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]）。<br />6. 如果卸載，請從磁片重載解決方案。<br />7. 將方案加入至原始檔控制。<br />8. 從原始檔控制解除方案的系結（使用 [**變更原始檔控制**] 對話方塊）。<br />9. 再次選取 [測試中的外掛程式]。<br />10. 如果卸載，請從磁片重載解決方案。<br />11. 將方案系結至原始位置（使用 [**變更**原始檔控制] 對話方塊）。 | 方案會使用選取的外掛程式加入至原始檔控制。 |

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)