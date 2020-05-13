---
title: XmlPoke 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b69afc20d15802ad79b201ca38e2d69f1d473b1e
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072489"
---
# <a name="xmlpoke-task"></a>XmlPoke 工作

將 XPath 查詢所指定的值設定至 XML 檔案。

## <a name="parameters"></a>參數

 下表說明 `XmlPoke` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`Namespaces`|選擇性的 `String` 參數。<br /><br /> 指定 XPath 查詢前置詞的命名空間。 `Namespaces` 是一個 XML 程式碼片段，由 `Namespace` 元素與 `Prefix` 和 `Uri` 屬性組成。 屬性 `Prefix` 會指定前置詞與 `Uri` 屬性中指定的命名空間建立關聯。 請勿使用空的 `Prefix`。|
|`Query`|選擇性的 `String` 參數。<br /><br /> 指定 XPath 查詢。|
|`Value`|必要的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要插入至指定路徑的值。|
|`XmlInputPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 將 XML 輸入指定為檔案路徑。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單,請參閱[工作延伸基項](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例

以下是要修改的 sample.xml：

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

在此範例中，若您想要修改 `/Package/mp:PhoneIdentity/PhoneProductId`，請使用

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` 在這裡的用途是預設命名空間的假造命名空間前置詞。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
