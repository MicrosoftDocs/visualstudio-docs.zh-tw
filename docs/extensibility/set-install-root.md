---
title: 使用 VSIX v3 在延伸資料夾外安裝 |微軟文件
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700175"
---
# <a name="install-outside-the-extensions-folder"></a>在延伸模組資料夾之外進行安裝

從 Visual Studio 2017 和 VSIX v3(版本 3)開始,可以在擴展資料夾之外安裝擴展資產。 目前,以下位置已啟用為有效的安裝位置(其中 [INSTALLDIR] 映射到 Visual Studio 實體的安裝目錄):

* [INSTALLDIR]_MSBuild
* [INSTALLDIR]\Xml_Schema
* [INSTALLDIR]_公共7_IDE_公共程式集
* [INSTALLDIR]=許可證
* [INSTALLDIR]=通用7_IDE_參考程式集
* [INSTALLDIR]_公共7_IDE_遠端除錯器
* [INSTALLDIR]_通用7_IDE_VC目標(僅適用於 2017 年視覺工作室;2019 年及以後用於視覺工作室)

> [!NOTE]
> VSIX 格式不允許在 Visual Studio 安裝資料夾結構之外安裝。 

為了支援安裝到這些目錄,VSIX 必須"每台計算機按實例安裝"。 這可以通過選中擴展中的「所有使用者」複選框來啟用。

![檢查所有使用者](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>如何設定安裝根

要設置安裝目錄,可以使用 Visual Studio 中的 **「屬性**」視窗。 例如,您可以將專案引用`InstallRoot`的屬性設定為上述位置之一:

![安裝根屬性](media/install-root-properties.png)

這將在 VSIX`ProjectReference`專案的 .csproj 檔內向相應的屬性新增一些元資料:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> 如果您願意,可以直接編輯 .csproj 檔。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>如何在「安裝根」下設定子路徑

如果要安裝到 下面的子路徑`InstallRoot`,`VsixSubPath`可以通過`InstallRoot`設置 屬性與 屬性類似來執行此操作。 例如,假設我們希望專案引用的輸出安裝到『[INSTALLDIR]MSBuild_MyCompany_MySDK_1.0'。 我們可以輕鬆地與屬性設計師一起執行此操作:

![設定子路徑](media/set-subpath.png)

相應的 .csproj 更改如下所示:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>額外資訊

屬性設計器更改不僅適用於專案引用,還應用於專案引用。也可以設置專案內`InstallRoot`專案的元數據(使用上述相同的方法)。
