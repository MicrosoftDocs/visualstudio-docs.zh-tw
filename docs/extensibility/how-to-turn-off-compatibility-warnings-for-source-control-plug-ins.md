---
title: 關閉原始檔控制外掛程式的警告
description: 在 Visual Studio 中使用原始檔控制時，使用者可能會看到數個相容性警告。 瞭解如何停用這些警告。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5607f4a92a14b692f20d509e014991d461815bd
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993545"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>如何：關閉原始檔控制外掛程式的相容性警告

使用中的原始檔控制時，使用者可能會看到數個相容性警告 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 所顯示的警告取決於原始檔控制外掛程式的功能，您可以依照此處的詳細說明來加以停用。

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>若要停用警告：「確保與 Visual Studio 的最佳原始檔控制整合」

- 如有必要，請設定下列登錄專案 (新增值) ：

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword：00000001**

   所有非外掛程式都會顯示此警告 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 。

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>若要停用警告：「安裝的原始檔控制提供者不支援所有功能」

- 如有必要，請設定下列兩個登錄值 (新增值) ：

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword：00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword：00000001**

     如果原始檔控制外掛程式未明確支援多個專案的重新進入，則會顯示此警告 (也就是，如果一次只能簽入一個檔案和專案) 。

     最好支援重新進入 (的 `SCC_CAP_REENTRANT` 功能) ; 這樣做會移除此警告。 但是，如果無法進行這項支援，則可以設定這些登錄專案。

## <a name="see-also"></a>另請參閱

- [功能旗標](../extensibility/capability-flags.md)
