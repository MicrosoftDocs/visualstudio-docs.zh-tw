---
title: WPF .Targets 檔案 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- combining tasks into a .targets file to build an MSBuild project [WPF MSBuild]
- WPF .targets files [WPF MSBuild], introduction
- WPF .targets files [WPF MSBuild]
ms.assetid: e85a3ff4-dedd-4ff4-9b22-3a1e94755362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 698ce78d9358b866a31d9af7cc7fbcba6d299667
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936577"
---
# <a name="wpf-targets-files"></a>WPF .targets 檔案
[!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] 會透過新增一組 [!INCLUDE[TLA2#tla_wpf](../msbuild/includes/tla2sharptla_wpf_md.md)] 特定的工作來延伸 [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]，這些工作已合併到特殊的 *.targets* 檔案 (*Microsoft.WinFX.targets*) 中。 此檔案會合併一組在 [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] 中建置 [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] 專案所需的 [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] 工作。  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild .targets 檔案](../msbuild/msbuild-dot-targets-files.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [建置 WPF 應用程式 (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)