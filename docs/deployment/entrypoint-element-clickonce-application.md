---
title: '&lt;entryPoint&gt;項目 （ClickOnce 應用程式） |Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 615a606dc4d04682a9d5a1a69c91b4d2cd67de15
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665255"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint&gt;項目 （ClickOnce 應用程式）
識別應該是組件時執行這[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]用戶端電腦上執行應用程式。

## <a name="syntax"></a>語法

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
 `entryPoint` 項目是必要的，且位於 `urn:schemas-microsoft-com:asm.v2` 命名空間。 只能有一個`entryPoint`應用程式資訊清單中所定義的項目。

 `entryPoint` 項目具有下列屬性。

|屬性|描述|
|---------------|-----------------|
|`name`|選擇性。 此值不使用.NET Framework。|

 `entryPoint` 具有下列項目。

## <a name="assemblyidentity"></a>assemblyIdentity
 必要項。 所扮演的角色`assemblyIdentity`和其屬性定義於[\<組件識別 > 項目](../deployment/assemblyidentity-element-clickonce-application.md)。

 `processorArchitecture`這個項目的屬性和`processorArchitecture`中所定義的屬性`assemblyIdentity`其他位置中應用程式資訊清單必須相符。

## <a name="commandline"></a>commandLine
 必要項。 必須是子系`entryPoint`項目。 它沒有任何子項目，並具有下列屬性。

| 屬性 | 描述 |
|--------------| - |
| `file` | 必要項。 啟動組件的本機參考[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 此值不能包含正斜線 （/） 或反斜線 (\\) 路徑分隔符號。 |
| `parameters` | 必要項。 描述要使用的進入點所採取的動作。 唯一有效的值是`run`; 如果提供了空白的字串，`run`假設。 |

## <a name="customhostrequired"></a>customHostRequired
 選擇性。 如果包含此項目，指定此部署包含將自訂主機，內部部署的元件，並不是獨立的應用程式。

 如果此項目，則`assemblyIdentity`和`commandLine`項目也必須有。 如有需要，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]將會在安裝期間引發驗證錯誤。

 這個項目會有任何屬性和任何子系。

## <a name="customux"></a>customUX
 選擇性。 指定的應用程式安裝和維護自訂的安裝程式中，並不會建立開始功能表項目、 快顯或新增或移除程式 項目。

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 包含 customUX 元素的應用程式必須提供自訂的安裝程式使用<xref:System.Deployment.Application.InPlaceHostingManager>類別來執行安裝作業。 按兩下其資訊清單或 setup.exe 必要啟動載入器無法安裝應用程式與這個項目。 開始功能表項目、 捷徑和新增或移除程式項目，可以建立自訂安裝程式。 如果自訂安裝程式不會建立一個新增或移除程式項目，它必須儲存所提供的訂用帳戶識別碼<xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A>屬性，並啟用使用者稍後解除安裝應用程式，藉由呼叫<xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A>方法。 如需詳細資訊，請參閱[逐步解說：為 ClickOnce 應用程式建立自訂安裝程式](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)。

## <a name="remarks"></a>備註
 此項目識別的組件和項目點[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。

 您無法使用`commandLine`將參數傳遞至您的應用程式在執行階段。 您可以存取的查詢字串參數[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]從應用程式的部署<xref:System.AppDomain>。 如需詳細資訊，請參閱[如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)。

## <a name="example"></a>範例
 下列程式碼範例說明`entryPoint`的應用程式資訊清單中的項目[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式。 此程式碼範例是針對提供之較大範例的一部分[Ndptecclick](../deployment/clickonce-application-manifest.md)主題。

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
