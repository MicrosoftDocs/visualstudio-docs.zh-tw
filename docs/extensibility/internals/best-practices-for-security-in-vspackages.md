---
title: Vspackage 中安全性的最佳作法 |Microsoft Docs
description: 瞭解 VSPackage 中安全性的最佳作法，也就是 Visual Studio 應用程式的基本安全性和部署單位。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cca66d6c1fce0deb8103a7d626c16a4e81bc7b5f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086205"
---
# <a name="best-practices-for-security-in-vspackages"></a>Vspackage 中安全性的最佳作法
若要 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 在您的電腦上安裝，您必須在具有系統管理認證的內容中執行。 應用程式的基本安全性和部署單位 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 是 [VSPackage](../../extensibility/internals/vspackages.md)。 VSPackage 必須使用註冊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，這也需要系統管理認證。

 系統管理員具有寫入登錄和檔案系統的完整許可權，並可執行任何程式碼。 您必須擁有這些許可權才能開發、部署或安裝 VSPackage。

 一旦安裝之後，VSPackage 就會完全受到信任。 由於這是與 VSPackage 相關聯的高層級許可權，因此可能會不慎安裝具有惡意意圖的 VSPackage。

 使用者應確保他們只會從信任的來源安裝 Vspackage。 開發 Vspackage 的公司應強式名稱並簽署它們，以確保防止使用者進行篡改。 開發 Vspackage 的公司應檢查其外部相依性（例如 web 服務和遠端安裝），以評估並修正任何安全性問題。

 如需詳細資訊，請參閱 [.NET Framework 的安全程式碼撰寫方針](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90))。

## <a name="see-also"></a>另請參閱
- [增益集安全性](/previous-versions/1326zbk3(v=vs.140))
- [DDEX 安全性](/previous-versions/bb163703(v=vs.140))