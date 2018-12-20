---
title: 容器的已知問題
description: 深入了解當您將 Visual Studio Build Tools 2017 安裝到 Windows 容器時，可能發生的已知問題。
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 529d967f34a5c99c8416058acad317cdc47d1053
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158615"
---
# <a name="known-issues-for-containers"></a>容器的已知問題

將 Visual Studio 安裝到 Docker 容器時有幾個問題。

## <a name="windows-container"></a>Windows 容器

當您將 Visual Studio Build Tools 2017 安裝到 Windows 容器時，會發生下列已知問題。

* 您無法將 Visual Studio 安裝到以映像 microsoft/windowsservercore:10.0.14393.1593 為基礎的容器。 以更舊或更新的 Windows 版本標記的映像應該會運作正常。
* 您無法安裝早於 10.0.14393 的 Windows SDK 版本。 某些套件無法安裝，且相依於這些套件的工作負載將無法運作。
* 建立映像時，請傳遞 `-m 2GB` (或以上)。 某些工作負載在安裝時，需要比預設 1 GB 更多的記憶體。
* 請設定 Docker 使用大於預設 20 GB 的磁碟。
* 在命令列上傳遞 `--norestart`。 在撰寫本文時，嘗試從容器內重新啟動 Windows 容器會傳回 `ERROR_TOO_MANY_OPEN_FILES` 給主機。
* 如果您讓映像直接以 microsoft/windowsservercore 為基礎，.NET Framework 可能無法正確安裝，且不會指出任何安裝錯誤。 安裝完成之後，可能無法執行受控碼。 相反地，讓您的映像以 [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) 或更新版本為基礎。 例如，使用 MSBuild 建置時，可能會看到這樣的錯誤：

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5)：錯誤 MSB6003：無法執行指定的工作可執行檔 "csc.exe"。 無法載入檔案或組件 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' 或其中一個相依性。 系統找不到指定的檔案。

## <a name="build-tools-container"></a>建置工具容器

當您使用建置工具容器時，可能會發生下列已知問題。 若要查看問題是否已獲得修正，或是否有其他已知問題，請瀏覽 https://developercommunity.visualstudio.com。

* 在[某些情況](https://github.com/Microsoft/vstest/issues/940)下，IntelliTrace 在容器內可能無法運作。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [將建置工具安裝至容器](build-tools-container.md)
* [容器的進階範例](advanced-build-tools-container.md)
* [Visual Studio Build Tools 2017 工作負載和元件識別碼](workload-component-id-vs-build-tools.md)
