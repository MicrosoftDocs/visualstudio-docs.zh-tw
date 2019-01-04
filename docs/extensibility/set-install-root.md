---
title: VSIX v3 的擴充功能資料夾之外進行安裝 |Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 847ce9bc55e93f292ffdfe6f237e8c39eeac9fd4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968494"
---
# <a name="installing-outside-the-extensions-folder"></a>擴充功能資料夾之外進行安裝

開始使用 Visual Studio 2017 和 VSIX v3 （第 3 版），現可支援安裝資料夾以外的延伸模組的延伸模組資產。 目前，下列位置啟用 （[INSTALLDIR] 會對應至 Visual Studio 執行個體的安裝目錄） 的有效的安裝位置為：

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets

>**注意：** VSIX 格式不允許您安裝 VS 安裝資料夾結構之外。

為了支援安裝這些目錄，VSIX 必須安裝 「 每個執行個體每台電腦 」。 這可藉由 extension.vsixmanifest 設計工具中的 [所有使用者] 核取都方塊來啟用：

![檢查所有的使用者](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>如何設定 InstallRoot

若要設定的安裝目錄，您可以使用**屬性**Visual Studio 中的視窗。 比方說，您可以設定`InstallRoot`屬性的其中一個上述位置的專案參考：

![安裝根屬性](media/install-root-properties.png)

這會將一些中繼資料新增至對應`ProjectReference`VSIX 專案的.csproj 檔案內的屬性：

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**注意：** 如果您想，您可以直接編輯.csproj 檔案。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>如何設定下的 InstallRoot 子路徑

如果您想要安裝到子路徑底下`InstallRoot`，則可以藉由設定`VsixSubPath`屬性就像`InstallRoot`屬性。 比方說，假設我們想要安裝到我們的專案參考輸出 ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'。 我們可以這麼輕鬆地與屬性設計工具：

![設定子路徑](media/set-subpath.png)

對應的.csproj 變更看起來像這樣：

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>額外的資訊

屬性設計工具變更適用於不只是專案參考;您可以設定`InstallRoot`以及您的專案內的項目中繼資料 （使用上面所述的相同方法）。
