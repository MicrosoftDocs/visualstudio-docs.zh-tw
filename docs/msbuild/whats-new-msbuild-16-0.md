---
title: MSBuild 16.0 的新功能 |Microsoft Docs
description: 瞭解 MSBuild 16.0 的已變更和更新功能和屬性，並連結至版本資訊。
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: cdfb552c53a40b6ad2f2349556396475926900be
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848249"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0 的新功能

此文章說明 MSBuild 16.0 的更新功能和屬性。 如需詳細的版本資訊，請參閱 [ MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831)。

## <a name="changed-path"></a>已變更的路徑

 MSBuild 會安裝在每個 Visual Studio 版本下的 *\Current* 資料夾中，而且可執行檔位於 *\bin* 子資料夾中。 例如，與 Visual Studio 2019 社區一起安裝 *MSBuild.exe* 的路徑是 *C:\Program Files (X86) \Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* 您也可以使用下列 PowerShell 模組來尋找 MSBuild： [vssetup.powershell。](https://github.com/Microsoft/vssetup.powershell)

## <a name="changed-properties"></a>已變更的屬性

 因為新的版本編號，所以已更新下列 MSBuild 屬性。

- 這個工具版本的 `MSBuildToolsVersion` 為 "Current"。 組件版本則與 Visual Studio 2017 的一樣，為 15.1.0.0。

- 這個工具版本的 `VisualStudioVersion` 為 "16.0"。

## <a name="change-waves"></a>變更波浪

從 MSBuild 16.8 開始，您可以選擇性地選擇是否要退出 MSBuild 中的特定潛在干擾性變更。 請參閱 [變更波浪](change-waves.md)。

## <a name="updates"></a>更新

MSBuild (與 Visual Studio) 現在以 .NET Framework 4.7.2 為目標。 若要使用新的 MSBuild API 功能，您的組件也必須升級，但現有的程式碼將繼續運作。

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
