---
title: 用作搜尋原始碼管理外掛程式的鍵的字串 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9333ff1b6742ca14dc5541bd15e92b2eb39085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699707"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>用作索引鍵以尋找原始檔控制外掛程式的字串
以下字串是訪問註冊表以查找有關原始程式碼管理外掛程式的資訊。

 `STR_SCC_PROVIDER_REG_LOCATION`,是註冊表項或用於將 DLL 註冊為 Visual Studio 的`STR_SCCPROVIDERPATH`原始程式碼管理外掛程式。 `STR_PROVIDERREGKEY` `STR_SCCPROVIDERNAME`

 `SCC_PROJECTNAME_KEY`,和用於描述 MSSCCPRJ`SCC_KEY, SCC_FILE_SIGNATURE`的格式。 `SCC_PROJECTAUX_KEY` `SCC_STATUS_FILE`SCC 檔。

## <a name="string-keys-and-values"></a>字串鍵與值

|Key|值|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|軟體_原始碼控制提供者|
|`STR_PROVIDERREGKEY`|提供者註冊金鑰|
|`STR_SCCPROVIDERPATH`|SCCServer路徑|
|`STR_SCCPROVIDERNAME`|SCCServer 名稱|
|`STR_SCC_INI_SECTION`|原始程式碼控制|
|`STR_SCC_INI_KEY`|原始碼管理者|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ.Scc|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|原始碼控制檔案|
|`SCC_NSE`|命名空間延伸|
|`SCC_NSE_PREFIX`|原前置|
|`SCC_NSE_DisableOpenSCC`|關閉開源源控制|
|`STR_SCCHELPCOLLECTION`|說明收集|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|軟體\微軟_來源安全|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [如何：安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)
