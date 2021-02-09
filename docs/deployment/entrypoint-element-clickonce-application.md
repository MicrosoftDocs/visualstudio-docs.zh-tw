---
title: '&lt;&gt; (ClickOnce 應用程式) 的 entryPoint 元素 |Microsoft Docs'
description: EntryPoint 元素會識別在用戶端電腦上執行此 ClickOnce 應用程式時應執行的元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5c35d94001ae1e883e2bd76650f248d7e0364d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893889"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;&gt; (ClickOnce 應用程式) 的 entryPoint 元素
識別在 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 用戶端電腦上執行此應用程式時應執行的元件。

## <a name="syntax"></a>Syntax

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## <a name="elements-and-attributes"></a>元素和屬性
 `entryPoint` 項目是必要的，且位於 `urn:schemas-microsoft-com:asm.v2` 命名空間。 `entryPoint`應用程式資訊清單中可能只會定義一個元素。

 `entryPoint` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`name`|選擇性。 .NET Framework 不會使用這個值。|

 `entryPoint` 具有下列項目。

## <a name="assemblyidentity"></a>assemblyIdentity
 必要。 `assemblyIdentity`和其屬性的角色定義于[ \<assemblyIdentity> 元素](../deployment/assemblyidentity-element-clickonce-application.md)中。

 `processorArchitecture`這個元素的屬性和 `processorArchitecture` `assemblyIdentity` 應用程式資訊清單中其他位置所定義的屬性必須相符。

## <a name="commandline"></a>commandLine
 必要。 必須是元素的子系 `entryPoint` 。 它沒有子項目，而且具有下列屬性。

| 屬性 | 描述 |
|--------------| - |
| `file` | 必要。 應用程式啟動元件的本機參考 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 此值不能包含正斜線 (/) 或反斜線 (\\) 路徑分隔符號。 |
| `parameters` | 必要。 描述進入點所要採取的動作。 唯一有效的值是 `run` ; 如果提供空字串， `run` 則會假設為。 |

## <a name="customhostrequired"></a>customHostRequired
 選擇性。 如果包含，則指定此部署包含將在自訂主機內部署的元件，而不是獨立的應用程式。

 如果這個元素存在， `assemblyIdentity` 和 `commandLine` 元素也不可以同時存在。 如果是， [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 則會在安裝期間引發驗證錯誤。

 此元素沒有屬性和子系。

## <a name="customux"></a>customUX
 選擇性。 指定應用程式是由自訂安裝程式所安裝和維護，而且不會建立 [開始] 功能表專案]、[快捷方式] 或 [新增或移除程式] 專案。

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 包含 customUX 元素的應用程式必須提供使用 <xref:System.Deployment.Application.InPlaceHostingManager> 類別來執行安裝作業的自訂安裝程式。 使用這個元素的應用程式無法藉由按兩下其資訊清單或 setup.exe 必要條件啟動載入器安裝。 自訂安裝程式可以建立 [開始] 功能表專案、快捷方式和 [新增或移除程式] 專案。 如果自訂安裝程式未建立 [新增或移除程式] 專案，它必須儲存屬性所提供的訂用帳戶識別碼 <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> ，並讓使用者稍後藉由呼叫方法來卸載應用程式 <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> 。 如需詳細資訊，請參閱 [逐步解說：為 ClickOnce 應用程式建立自訂安裝](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)程式。

## <a name="remarks"></a>備註
 這個元素會識別應用程式的元件和進入點 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

 您無法 `commandLine` 在執行時間使用將參數傳遞至應用程式。 您可以從應用程式存取部署的查詢字串參數 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] <xref:System.AppDomain> 。 如需詳細資訊，請參閱 [如何：在線上 ClickOnce 應用程式中取得查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。

## <a name="example"></a>範例
 下列程式碼範例說明 `entryPoint` 應用程式之應用程式資訊清單中的元素 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 這個程式碼範例是針對 [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md) 主題提供之較大範例的一部分。

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## <a name="see-also"></a>另請參閱
- [ClickOnce 應用程式資訊清單](../deployment/clickonce-application-manifest.md)
