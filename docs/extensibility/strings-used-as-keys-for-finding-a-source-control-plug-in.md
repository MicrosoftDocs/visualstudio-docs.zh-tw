---
title: 用來做為尋找原始檔控制外掛程式之索引鍵的字串 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07962ff9e0f9371b1fc308a35600a6819602b4f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719457"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>用作索引鍵以尋找原始檔控制外掛程式的字串
下列字串是用來存取登錄的索引鍵，以尋找原始檔控制外掛程式的相關資訊。

 `STR_SCC_PROVIDER_REG_LOCATION`、`STR_PROVIDERREGKEY`、`STR_SCCPROVIDERPATH` 和 `STR_SCCPROVIDERNAME` 是登錄機碼或值，用來註冊 DLL 作為 Visual Studio 的原始檔控制外掛程式。

 `SCC_PROJECTNAME_KEY`、`SCC_PROJECTAUX_KEY`、`SCC_KEY, SCC_FILE_SIGNATURE` 和 `SCC_STATUS_FILE` 是用來描述 MSSCCPRJ.SCC 的格式。SCC 檔案。

## <a name="string-keys-and-values"></a>字串索引鍵和值

|機碼|值|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|原始程式碼控制|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ.SCC.SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|原始程式碼控制檔案|
|`SCC_NSE`|命名空間延伸模組|
|`SCC_NSE_PREFIX`|Protocal 前置詞|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|N|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [如何：安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)