---
title: 測試區域8：外掛程式切換 |Microsoft Docs
description: 此原始檔控制測試區域提供的測試案例，可讓您在 Visual Studio 中挑選要用於方案原始檔控制的外掛程式。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b6c3a25aa9312073d3ce4a60752d41585fcee7b3
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487643"
---
# <a name="test-area-8-plug-in-switching"></a>測試區域 8：外掛程式切換
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 具有使用者介面 (UI) ，可變更目前的原始檔控制外掛程式。 這個測試區域提供的測試案例，可讓您挑選要用於方案原始檔控制的外掛程式。

## <a name="command-menu-access"></a>命令功能表存取
 下列 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境功能表路徑用於測試案例中。

- 目前的原始檔控制外掛程式：**工具**  ->  **選項**  ->  **原始檔控制**  ->  **外掛程式選取專案**。

- 變更原始檔控制系 **結：檔案**  ->  **原始** 檔控制  ->  **變更原始檔控制**.。。

## <a name="common-expected-behavior"></a>常見的預期行為
 您可以變更解決方案的原始檔控制外掛程式，而不需要離開 Visual Studio 或重載方案。 此外，當載入方案時，目前的原始檔控制外掛程式會自動變更為方案所使用的外掛程式。

## <a name="test-cases"></a>測試案例
 以下是外掛程式切換測試區域的特定測試案例。

### <a name="case-8a-automatic-change"></a>案例8a：自動變更

#### <a name="expected-behavior"></a>預期行為
 當使用者載入原始檔控制下的方案時，會自動載入方案，並將適當的原始檔控制外掛程式選取為 [目前]。

| 動作 | 測試步驟 | 要驗證的預期結果 |
| - | - | - |
| 自動原始檔控制外掛程式變更 | 1. 選取 [測試中的外掛程式] 作為 [目前的 (**工具**  ->  **選項**  ->    ->  **] 選取 [** 原始檔控制] 選項。 ) <br />2. 建立新專案。<br />3. 將方案加入至原始檔控制。<br />4. 選取其他外掛程式 (例如 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]) 。<br />5. 接受卸載解決方案提示。<br />6. 從磁片重新開啟解決方案。 | 方案已開啟。<br /><br /> 受測試的外掛程式是目前的原始檔控制外掛程式。 |

### <a name="case-8b-solution-based-change"></a>案例8b：以方案為基礎的變更

#### <a name="expected-behavior"></a>預期行為
 解決方案可以變更其相關聯的原始檔控制外掛程式。

| 動作 | 測試步驟 | 要驗證的預期結果 |
|----------------------------------| - | - |
| 變更解決方案的外掛程式 | 1. 選取 [目前測試中的外掛程式] 作為 [目前 (**工具**  ->  **選項**]  ->    ->  ) 的 [選項]。<br />2. 建立新的專案和方案。<br />3. 將方案加入至原始檔控制。<br />4. 使用 [ **變更原始檔控制** ] 對話方塊，將方案從原始檔控制解除系結 () 。<br />5. 選取其他外掛程式 (例如 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]) 。<br />6. 如果卸載，請從磁片重載方案。<br />7. 將方案加入至原始檔控制。<br />8. 使用 [ **變更原始檔控制** ] 對話方塊，將方案從原始檔控制解除系結 () 。<br />9. 再次選取 [測試中的外掛程式]。<br />10. 如果卸載，請從磁片重載方案。<br />11. 使用 [變更原始檔 **控制** ] 對話方塊) ，將方案系結至原始位置 (。 | 解決方案會使用所選外掛程式新增至原始檔控制。 |

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式測試指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
