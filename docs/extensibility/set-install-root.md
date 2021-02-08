---
title: 使用 VSIX v3 在擴充功能資料夾外部安裝 |Microsoft Docs
description: 瞭解如何在延伸模組資料夾之外安裝 Visual Studio SDK 擴充資產，以及哪些位置有效。
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0a6e955d2ceb4ef8f4f2d4edcd8221badee8caf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836653"
---
# <a name="install-outside-the-extensions-folder"></a>在延伸模組資料夾之外進行安裝

從 Visual Studio 2017 和 VSIX v3 (第3版) 開始，延伸模組資產可以安裝在延伸模組資料夾之外。 目前，下列位置會啟用為有效的安裝位置 (其中 [INSTALLDIR] 對應至 Visual Studio 實例的安裝目錄) ：

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (僅支援 Visual Studio 2017;已淘汰 Visual Studio 2019 和更新版本) 

> [!NOTE]
> VSIX 格式不允許您在 Visual Studio 安裝資料夾結構之外進行安裝。 

為了支援安裝到這些目錄，必須將 VSIX 安裝為「每個實例的每部電腦」。 您可以勾選 extension.vsixmanifest 設計師中的 [所有使用者] 核取方塊來啟用此功能：

![檢查所有使用者](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>如何設定 InstallRoot

若要設定安裝目錄，您可以使用 Visual Studio 中的 [ **屬性** ] 視窗。 例如，您可以將 `InstallRoot` 專案參考的屬性設定為上述其中一個位置：

![安裝根屬性](media/install-root-properties.png)

這會將一些中繼資料新增至 `ProjectReference` VSIX 專案 .csproj 檔案內的對應屬性：

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> 如果您想要的話，也可以直接編輯 .csproj 檔案。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>如何設定 InstallRoot 底下的子路徑

如果您想要安裝至底下的子路徑 `InstallRoot` ，可以設定 `VsixSubPath` 屬性，就像 `InstallRoot` 屬性一樣。 比方說，假設我們想要將專案參考的輸出安裝到 ' [INSTALLDIR] \MSBuild\MyCompany\MySDK\1.0 '。 我們可以使用屬性設計工具輕鬆完成此作業：

![設定子路徑](media/set-subpath.png)

對應的 .csproj 變更看起來會像這樣：

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>額外資訊

屬性設計工具變更只適用于專案參考;您也可以 `InstallRoot` 使用上述) 所述的相同方法，來設定 (專案內專案的中繼資料。
