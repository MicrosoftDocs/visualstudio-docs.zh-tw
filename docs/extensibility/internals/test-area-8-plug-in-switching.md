---
title: 測試區域 8:外掛程式切換 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704397"
---
# <a name="test-area-8-plug-in-switching"></a>測試區域 8︰外掛程式切換
整合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]式開發環境 (IDE) 具有更改目前原始程式碼管理外掛程式的使用者介面 (UI)。 此測試區域為選取用於解決方案原始程式碼管理的外掛程式的過程提供了測試用例。

## <a name="command-menu-access"></a>命令選單存取
 測試用例[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中使用了以下集成開發環境功能表路徑。

- 目前原始碼管理外掛程式:**工具** -> **選項** -> **源碼管理** -> **外掛程式選擇**。

- 變更原始碼管理系統:**檔案** -> **碼管理** -> **變更原始碼管理**...

## <a name="common-expected-behavior"></a>常見預期行為
 無需退出 Visual Studio 或重新載入解決方案,即可更改解決方案的原始程式碼管理外掛程式。 此外,目前原始程式管理外掛程式會在載入解決方案時自動更改為解決方案使用。

## <a name="test-cases"></a>測試案例
 以下是外掛程式切換測試區域的特定測試用例。

### <a name="case-8a-automatic-change"></a>案例 8a:自動變更

#### <a name="expected-behavior"></a>預期行為
 當使用者載入受原始程式碼管理的解決方案時,將自動載入解決方案,並將適當的原始程式碼管理外掛程式選擇為當前外掛程式。

| 動作 | 測試步驟 | 要驗證的預期結果 |
| - | - | - |
| 自動源碼管理外掛程式變更 | 1. 選擇被測試的外掛程式作為目前外掛程式(**工具** -> **選項** -> **源碼管理** -> **外掛程式選擇**.)<br />2. 創建新專案。<br />3. 將解決方案添加到原始程式碼管理。<br />4. 選擇另一個外掛程式([!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]例如, .<br />5. 接受卸載解決方案提示。<br />6. 從磁碟重新打開解決方案。 | 解決方案已打開。<br /><br /> 正在測試的外掛程式是目前原始程式管理外掛程式。 |

### <a name="case-8b-solution-based-change"></a>案例 8b:基於解決方案的變更

#### <a name="expected-behavior"></a>預期行為
 解決方案可以更改其關聯的原始程式碼管理外掛程式。

| 動作 | 測試步驟 | 要驗證的預期結果 |
|----------------------------------| - | - |
| 為解決方案更改外掛程式 | 1. 選擇被測試的外掛程式作為目前 (**工具** -> **選項** -> **源碼管理** -> **外掛程式選擇**).<br />2. 創建新專案和解決方案。<br />3. 將解決方案添加到原始程式碼管理。<br />4. 從原始碼管理取消綁定解決方案(使用**更改原始程式碼管理**對話方塊)。<br />5. 選擇另一個外掛程式([!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]例如, .<br />6. 如果卸載,將從磁碟重新載入解決方案。<br />7. 將解決方案添加到原始程式碼管理。<br />8. 從原始程式碼管理取消綁定解決方案(使用**更改原始程式碼管理**對話方塊)。<br />9. 再次選擇正在測試的外掛程式。<br />10. 如果卸載,則從磁碟重新載入解決方案。<br />11. 將解決方案繫結到原始位置(使用 **"更改源控制"** 對話框)。 | 使用選擇外掛程式將解決方案添加到原始程式碼管理中。 |

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
