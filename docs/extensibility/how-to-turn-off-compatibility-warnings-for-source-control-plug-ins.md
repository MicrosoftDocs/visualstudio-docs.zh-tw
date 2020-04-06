---
title: 關閉源控制外掛程式的相容性警告 |微軟文件
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
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710718"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>如何:關閉原始碼管理外掛程式的相容性警告
在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中 使用原始碼時,使用者可能會看到多個相容性警告。 顯示的警告取決於原始程式碼管理外掛程式的功能,可以在此處禁用,如下所示。

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>禁用警告:"確保與 Visual Studio 的最佳源代碼管理集成"

- 設定以下註冊表項(如有必要,添加值):

   **HKEY_CURRENT_USER_軟體_微軟_VisualStudio_8.0_原始程式碼控制\不要顯示檢查DotNET相容 = dword:0000001**

   將顯示此警告,用於所有非[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]外掛程式。

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>禁用警告:"已安裝的原始程式碼管理提供程式不支援所有功能"

- 設定以下兩個註冊表值(如有必要添加值):

     **HKEY_CURRENT_USER_軟體\微軟_VisualStudio_8.0_原始程式碼控制\警告OldMSSCCI提供者 = dword:0000000**

    **HKEY_CURRENT_USER_軟體\微軟_VisualStudio_8.0_原始程式碼控制\使用OldSCC = dword:00000001**

     如果原始程式碼管理外掛程式不顯式支援多個專案的重化(也就是說,如果一次只能簽入一個檔和專案),則顯示此警告。

     最好支援重化(`SCC_CAP_REENTRANT`能力);這樣做將刪除此警告。 但是,如果無法進行此支援,則可以設置這些註冊表項。

## <a name="see-also"></a>另請參閱
- [功能旗標](../extensibility/capability-flags.md)
