---
title: VS 包中安全最佳實踐 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709899"
---
# <a name="best-practices-for-security-in-vspackages"></a>VS 套件中的安全最佳實務
要在電腦上[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]安裝 , 必須在具有管理認證的上下文中執行。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]應用程式的安全和部署的基本單位是[VSPackage。](../../extensibility/internals/vspackages.md) VSPackage 必須使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]註冊 ,這也需要管理憑據。

 管理員具有寫入註冊表和文件系統以及運行任何代碼的完整許可權。 您必須具有這些許可權才能開發、部署或安裝 VS 包。

 一旦安裝,VSPackage 即完全受信任。 由於與 VSPackage 關聯的這種高級別許可權,因此可能會無意中安裝具有惡意的 VSPackage。

 用戶應確保僅從受信任的源安裝 VS 包。 開發 VSPackages 的公司應牢固地命名並簽署它們,以確保使用者防止篡改。 開發 VSPackages 的公司應檢查其外部依賴項(如 Web 服務和遠端安裝),以評估和糾正任何安全問題。

 有關詳細資訊,請參閱[.NET 框架的安全編碼準則](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90))。

## <a name="see-also"></a>另請參閱
- [外接程式安全性](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [DDEX 安全性](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
