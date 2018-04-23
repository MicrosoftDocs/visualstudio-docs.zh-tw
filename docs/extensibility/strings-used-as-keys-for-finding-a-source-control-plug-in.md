---
title: 字串做為索引鍵來尋找原始檔控制外掛程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a42eebe67ce1f611cf6e48883bc09139f241e658
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>字串做為索引鍵來尋找原始檔控制外掛程式
下列字串是索引鍵來存取此登錄來尋找資訊的原始檔控制外掛程式。  
  
 `STR_SCC_PROVIDER_REG_LOCATION``STR_PROVIDERREGKEY`， `STR_SCCPROVIDERPATH`，和`STR_SCCPROVIDERNAME`登錄機碼或用來做為原始檔控制外掛程式註冊 DLL，適用於 Visual Studio 的值。  
  
 `SCC_PROJECTNAME_KEY``SCC_PROJECTAUX_KEY`， `SCC_KEY, SCC_FILE_SIGNATURE`，和`SCC_STATUS_FILE`用來描述 MSSCCPRJ 的格式。SCC 檔案。  
  
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
|`SCC_STATUS_FILE`|MSSCCPRJ。SCC|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|原始程式碼控制檔|  
|`SCC_NSE`|命名空間擴充功能|  
|`SCC_NSE_PREFIX`|Protocal 前置詞|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [如何： 安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [MSSCCPRJ.SCC 檔案](../extensibility/mssccprj-scc-file.md)