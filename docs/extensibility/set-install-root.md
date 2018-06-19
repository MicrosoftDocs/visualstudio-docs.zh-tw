---
title: 安裝 VSIX v3 與擴充功能資料夾之外 |Microsoft 文件
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8476b300974d66efc60f647c897ec6892191e7fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136772"
---
# <a name="installing-outside-the-extensions-folder"></a>安裝擴充功能資料夾外

從 Visual Studio 2017 和 VSIX v3 （第 3 版），現可支援安裝擴充功能資料夾以外的延伸模組資產。 目前，做為有效的安裝位置 （[INSTALLDIR] 會對應至 Visual Studio 執行個體的安裝目錄），會啟用下列位置：

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets

>**注意：** VSIX 格式不允許您的 VS 安裝資料夾結構之外安裝。

為了支援安裝這些目錄，VSIX 必須安裝 「 個別執行個體每台機器 」。 這可以藉由檢查 extension.vsixmanifest 設計工具中的"all users"核取方塊啟用：

![檢查所有使用者](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>如何設定 InstallRoot

若要設定的安裝目錄，您可以使用**屬性**Visual Studio 中的視窗。 比方說，您可以設定`InstallRoot`上述位置的其中一個專案參考的屬性：

![安裝根屬性](media/install-root-properties.png)

這會將一些中繼資料加入至對應`ProjectReference`VSIX 專案.csproj 檔案內的屬性：

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**注意：** 您可以編輯.csproj 檔案直接，如果您偏好。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>如何設定 InstallRoot 底下的子路徑

如果您想要安裝到下方的子路徑`InstallRoot`，您可以藉由設定`VsixSubPath`屬性一樣`InstallRoot`屬性。 比方說，假設我們想要安裝到我們的專案參考輸出 ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'。 我們可以這樣做輕鬆地與屬性設計工具：

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

將屬性設計工具變更套用到不只是專案參考。您可以設定`InstallRoot`內以及專案項目的中繼資料 （使用上面所述的相同方法）。
