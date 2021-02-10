---
title: 如何：針對服務進行疑難排解 |Microsoft Docs
description: 瞭解如何疑難排解當您嘗試在 Visual Studio SDK 中取得服務時可能發生的幾個常見問題。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6e29f2c65ec7503f06baca4af4c6772090d5eb8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952287"
---
# <a name="how-to-troubleshoot-services"></a>如何：針對服務進行疑難排解
當您嘗試取得服務時，可能會發生幾個常見問題：

- 未向註冊服務 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

- 服務是由介面類別型所要求，而不是由服務類型要求。

- 要求服務的 VSPackage 尚未放置。

- 使用了錯誤的服務提供者。

  如果無法取得要求的服務，則呼叫會傳回 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> null。 要求服務之後，您應該一律測試 null：

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>針對服務進行疑難排解

1. 檢查系統登錄，查看是否已正確註冊服務。 如需詳細資訊，請參閱 how [to：提供服務](../extensibility/how-to-provide-a-service.md)。

    下列 *.reg* 檔案片段會顯示 SVsTextManager 服務的註冊方式：

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    在上述範例中，版本號碼是的版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] （例如12.0 或14.0），金鑰 {F5E7E71D-1401-11d1-883B-0000F87579D2} 是服務的服務識別碼 (SID) ，而預設值為 {F5E7E720-1401-11d1-883B-0000F87579D2} 是提供服務的文字管理員 VSPackage 套件 GUID。

2. 當您呼叫 GetService 時，請使用服務類型，而不是介面類別型。 從要求服務時 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，會 <xref:Microsoft.VisualStudio.Shell.Package> 從類型中解壓縮 GUID。 如果下列條件存在，就不會找到服務：

   1. 介面類別型會傳遞至 GetService，而不是服務類型。

   2. 未將 GUID 明確指派給介面。 因此，系統會視需要建立物件的預設 GUID。

3. 請確定要求服務的 VSPackage 已被放置。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage 在建立之後和呼叫之前的網站 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 。

    如果您的 VSPackage 函式中有需要服務的程式碼，請將它移至 `Initialize` 方法。

4. 請確定您使用的是正確的服務提供者。

    並非所有服務提供者都一樣。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]傳遞至工具視窗的服務提供者不同于它傳遞給 VSPackage 的服務提供者。 工具視窗服務提供者知道 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> ，但不知道 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> 。 您可以呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ，從工具視窗內取得 VSPackage 服務提供者。

    如果工具視窗裝載使用者控制項或任何其他控制項容器，此容器將由 Windows 元件模型放置，而且無法存取任何 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 服務。 您可以呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ，從控制項容器內取得 VSPackage 服務提供者。

## <a name="see-also"></a>另請參閱
- [可用服務的清單](../extensibility/internals/list-of-available-services.md)
- [使用和提供服務](../extensibility/using-and-providing-services.md)
- [服務基本概念](../extensibility/internals/service-essentials.md)
- [Visual Studio 疑難排解](/troubleshoot/visualstudio/welcome-visual-studio/)