---
title: 用來作為索引鍵以尋找原始檔控制外掛程式的字串
description: 瞭解用來存取登錄的索引鍵的字串，以尋找原始檔控制外掛程式的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b61c13973ac6668814fbc3ba076b373d6e0b1e44
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056294"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>用作索引鍵以尋找原始檔控制外掛程式的字串
下列字串是存取登錄以尋找原始檔控制外掛程式相關資訊的索引鍵。

 `STR_SCC_PROVIDER_REG_LOCATION`、 `STR_PROVIDERREGKEY` 、 `STR_SCCPROVIDERPATH` 和是登錄機 `STR_SCCPROVIDERNAME` 碼或值，可用來將 DLL 註冊為 Visual Studio 的原始檔控制外掛程式。

 `SCC_PROJECTNAME_KEY`、 `SCC_PROJECTAUX_KEY` 、 `SCC_KEY, SCC_FILE_SIGNATURE` 和 `SCC_STATUS_FILE` 會用來描述 mssccprj.scc 的格式。SCC 檔。

## <a name="string-keys-and-values"></a>字串索引鍵和值

|Key|值|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|原始程式碼控制|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ.SCC.Scc|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|原始程式碼控制檔案|
|`SCC_NSE`|命名空間延伸模組|
|`SCC_NSE_PREFIX`|通訊協定前置詞|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|N|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [如何：安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)
