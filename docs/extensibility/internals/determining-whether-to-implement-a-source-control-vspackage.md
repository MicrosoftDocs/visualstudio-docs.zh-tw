---
title: 確定是否實現原始碼管理 VS 套件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708726"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>確定是否實現原始碼管理 VSPackage
本節詳細介紹了原始程式碼管理外掛程式和原始程式碼管理 VSPackages 用於擴展原始程式碼管理解決方案的選擇,並給出了有關選擇適當整合路徑的廣泛指南。

## <a name="small-source-control-solution-with-limited-resources"></a>資源有限的小型原始程式碼管理解決方案
 如果資源有限,並且無法承擔編寫原始程式碼管理包的開銷,則可以創建基於原始程式碼管理外掛程式的外掛程式。這樣做允許您與原始程式碼管理包並行工作,並且可以按需在原始程式管理外掛程式和包之間切換。 有關詳細資訊,請參閱[註冊和選擇](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)。

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>具有豐富功能集的大型原始碼管理解決方案
 如果要實現源控制解決方案,該解決方案提供豐富的原始程式碼管理模型,但使用原始程式碼管理外掛程式 API 未充分捕捉,則可以將原始程式碼管理套件視為整合路徑。 這尤其適用於您希望將原始程式碼管理適配器套件(與原始程式碼管理外掛程式通訊並提供基本原始程式碼管理 UI)替換為您自己的,以便以自訂方式處理原始程式碼管理事件。 如果您已經有一個令人滿意的原始程式碼管理 UI,並希望[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在 中保留該體驗,原始程式碼管理包選項允許您做到這一點。 原始程式碼管理包不是通用的,僅用於 IDE。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

 如果要實現對原始程式碼管理邏輯和 UI 提供靈活性和更豐富的控制的原始程式碼管理解決方案,您可能更喜歡原始碼管理包集成路由。 您可以：

1. 註冊您自己的原始程式碼管理 VSPackage(請參閱[註冊和選擇](../../extensibility/internals/registration-and-selection-source-control-vspackage.md))。

2. 將預設原始碼管理 UI 替換為自訂 UI(請參閱[自訂使用者介面](../../extensibility/internals/custom-user-interface-source-control-vspackage.md))。

3. 指定要使用的字形並處理解決方案資源管理器字形事件(請參閱[字形控件](../../extensibility/internals/glyph-control-source-control-vspackage.md))。

4. 處理查詢編輯和查詢保存事件(請參閱[查詢編輯查詢保存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md))。

## <a name="see-also"></a>另請參閱
- [建立原始碼管理外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)
