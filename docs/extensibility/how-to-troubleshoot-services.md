---
title: 如何:故障排除服務 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710754"
---
# <a name="how-to-troubleshoot-services"></a>如何:故障排除服務
當您嘗試取得服務時,可能會出現幾個常見問題:

- 該服務未在中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]註冊。

- 該服務按介面類型請求,而不是按服務類型請求。

- 請求該服務的 VS 包尚未進行網站。

- 使用錯誤的服務提供者。

  如果無法取得請求的服務,則對呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>傳回 null。 要求服務後,應始終測試 null:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>對服務進行故障排除

1. 檢查系統註冊表以查看服務是否已正確註冊。 有關詳細資訊,請參閱[如何:提供服務](../extensibility/how-to-provide-a-service.md)。

    以下 *.reg*檔案片段顯示了如何註冊 SVTextManager 服務:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    在上面的示例中,版本號是[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]版本,如 12.0 或 14.0,密鑰 #F5E7E71D-1401-11d1-883B-00000F87579D2] 是服務的服務標識符 (SID), SVTextManager 和預設值 {F5E7E720-1401-11d1-883B-0000F87579D2} 是提供該服務的文本管理器 VSPackage 的包 GUID。

2. 在調用 GetService 時,請使用服務類型而不是介面類型。 從[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]要求服務時<xref:Microsoft.VisualStudio.Shell.Package>, 將從 類型中提取 GUID。 如果存在以下條件,將找不到服務:

   1. 介面類型傳遞給 GetService 而不是服務類型。

   2. 沒有顯式分配給介面的 GUID。 因此,系統根據需要為物件創建預設 GUID。

3. 確保請求該服務的 VSPackage 已已已網站。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在建構 VSPackage 後和<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>調用 之前對 VSPackage 進行網站。

    如果 VSPackage 建構函數中的代碼需要服務,請將其移`Initialize`至方法 。

4. 確保您使用的是正確的服務提供者。

    並非所有服務提供者都是一樣的。 傳遞到工具視窗的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]服務提供者不同於它傳遞給 VSPackage 的提供程式。 工具視窗服務提供者知道,<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>但不知道<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 您可以呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>從工具視窗中取得 VSPackage 服務供應商。

    如果工具視窗承載使用者控制項或任何其他控制項容器,則容器將由 Windows 元件模型設置,並且無法存[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]取任何服務。 您可以呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>從控制項容器中取得 VSPackage 服務供應商。

## <a name="see-also"></a>另請參閱
- [可用服務清單](../extensibility/internals/list-of-available-services.md)
- [使用與提供服務](../extensibility/using-and-providing-services.md)
- [服務要點](../extensibility/internals/service-essentials.md)
