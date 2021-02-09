---
title: ClickOnce 非受控 API 參考 |Microsoft Docs
description: 從 dfshim.dll 瞭解 ClickOnce 非受控公用 Api，包括 CleanOnlineAppCache、GetDeploymentDataFromManifest 和 LaunchApplication。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 88d8147dded05c6bec54682e76c6a8c1826b43e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900793"
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce 非受控 API 參考
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dfshim.dll 的非受控公用 Api。

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 清除或卸載應用程式快取中的所有線上應用程式 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。

### <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回表示失敗的 HRESULT。 如果發生 managed 例外狀況，則會傳回 0x80020009 (DISP_E_EXCEPTION) 。

### <a name="remarks"></a>備註
 呼叫 CleanOnlineAppCache 將會啟動 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 服務（如果尚未執行）。

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 從資訊清單和啟用 URL 抓取部署資訊。

### <a name="parameters"></a>參數

|參數|描述|類型|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|`ActivationURL` 的指標。|LPCWSTR|
|`pcwzPathToDeploymentManifest`|`PathToDeploymentManifest` 的指標。|LPCWSTR|
|`pwzApplicationIdentity`|緩衝區的指標，用來接收以 Null 終止的字串，指定傳回的完整應用程式識別。|LPWSTR|
|`pdwIdentityBufferLength`|DWORD 的指標，此為緩衝區的長度 `pwzApplicationIdentity` （以 WCHARs）。 這包括 Null 終止字元的空間。|LPDWORD|
|`pwzProcessorArchitecture`|緩衝區的指標，用來接收以 Null 終止的字串，此字串會從資訊清單中指定應用程式部署的處理器架構。|LPWSTR|
|`pdwArchitectureBufferLength`|DWORD 的指標，此為緩衝區的長度 `pwzProcessorArchitecture` （以 WCHARs）。|LPDWORD|
|`pwzApplicationManifestCodebase`|緩衝區的指標，用來接收以 Null 終止的字串，此字串會從資訊清單中指定應用程式資訊清單的程式碼基底。|LPWSTR|
|`pdwCodebaseBufferLength`|DWORD 的指標，此為緩衝區的長度 `pwzApplicationManifestCodebase` （以 WCHARs）。|LPDWORD|
|`pwzDeploymentProvider`|緩衝區的指標，用來接收以 Null 終止的字串，以指定資訊清單中的部署提供者（如果有的話）。 否則，會傳回空字串。|LPWSTR|
|`pdwProviderBufferLength`|DWORD 的指標，其為的長度 `pwzProviderBufferLength` 。|LPDWORD|

### <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回表示失敗的 HRESULT。 如果緩衝區太小，則傳回 HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) 。

### <a name="remarks"></a>備註
 指標不得為 null。 `pcwzActivationUrl` 和 `pcwzPathToDeploymentManifest` 不得空白。

 呼叫者必須負責清除啟用 URL。 例如，在需要時加入 escape 字元或移除查詢字串。

 呼叫端負責限制輸入長度。 例如，最大 URL 長度為2KB。

## <a name="launchapplication"></a>LaunchApplication
 使用部署 URL 來啟動或安裝應用程式。

### <a name="parameters"></a>參數

|參數|描述|類型|
|---------------|-----------------|----------|
|`deploymentUrl`|以 Null 結束的字串指標，其中包含部署資訊清單的 URL。|LPCWSTR|
|`data`|保留供未來使用。 必須是 Null。|LPVOID|
|`flags`|保留供未來使用。 必須是 0。|DWORD|

### <a name="return-value"></a>傳回值
 如果成功，則傳回 S_OK;否則，會傳回表示失敗的 HRESULT。 如果發生 managed 例外狀況，則會傳回 0x80020009 (DISP_E_EXCEPTION) 。

## <a name="see-also"></a>另請參閱
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>