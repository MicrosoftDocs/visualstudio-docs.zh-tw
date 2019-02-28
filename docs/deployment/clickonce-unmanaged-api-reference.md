---
title: ClickOnce Unmanaged API 參考 |Microsoft Docs
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3b536a17df4f54158aa6f157a0d9795cf359ddc0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633794"
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce 非受控 API 參考
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 從 dfshim.dll 未受管理的公用 Api。

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 清除或解除安裝所有的線上應用程式，從[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式快取。

### <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，會傳回 HRESULT，表示失敗。 如果 managed 例外狀況發生時，會傳回 0x80020009 (DISP_E_EXCEPTION)。

### <a name="remarks"></a>備註
 將會開始呼叫 CleanOnlineAppCache[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]服務如果尚未執行。

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 擷取部署資訊從資訊清單和啟用 URL。

### <a name="parameters"></a>參數

|參數|說明|類型|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|`ActivationURL` 的指標。|LPCWSTR|
|`pcwzPathToDeploymentManifest`|`PathToDeploymentManifest` 的指標。|LPCWSTR|
|`pwzApplicationIdentity`|收到 NULL 終止的字串，指定傳回完整的應用程式身分識別之緩衝區的指標。|LPWSTR|
|`pdwIdentityBufferLength`|長度為 DWORD 的指標`pwzApplicationIdentity`WCHARs 中的緩衝區。 這包括 NULL 結束字元的空間。|LPDWORD|
|`pwzProcessorArchitecture`|收到 NULL 終止的字串，指定處理器架構的應用程式部署，從資訊清單之緩衝區的指標。|LPWSTR|
|`pdwArchitectureBufferLength`|長度為 DWORD 的指標`pwzProcessorArchitecture`WCHARs 中的緩衝區。|LPDWORD|
|`pwzApplicationManifestCodebase`|以 NULL 終止的字串，指定應用程式資訊清單中，從資訊清單的程式碼基底的接收緩衝區的指標。|LPWSTR|
|`pdwCodebaseBufferLength`|長度為 DWORD 的指標`pwzApplicationManifestCodebase`WCHARs 中的緩衝區。|LPDWORD|
|`pwzDeploymentProvider`|接收以 NULL 結束的字串之緩衝區的指標，指定資訊清單中，從部署提供者，如果有的話。 否則，會傳回空字串。|LPWSTR|
|`pdwProviderBufferLength`|長度為 DWORD 的指標`pwzProviderBufferLength`。|LPDWORD|

### <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，會傳回 HRESULT，表示失敗。 如果緩衝區太小，則傳回 HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER)。

### <a name="remarks"></a>備註
 指標不得為 null。 `pcwzActivationUrl` 和`pcwzPathToDeploymentManifest`不得為空白。

 是呼叫者的責任，清除 啟用 URL。 例如，加入逸出字元的所需的位置，或移除查詢字串。

 它負責將呼叫者的輸入的長度限制。 例如，URL 長度上限為 2 KB。

## <a name="launchapplication"></a>LaunchApplication
 啟動或安裝應用程式所使用的部署 URL。

### <a name="parameters"></a>參數

|參數|說明|類型|
|---------------|-----------------|----------|
|`deploymentUrl`|以 NULL 終止的字串，其中包含部署資訊清單 URL 的指標。|LPCWSTR|
|`data`|保留供未來使用。 必須是 Null。|LPVOID|
|`flags`|保留供未來使用。 必須是 0。|DWORD|

### <a name="return-value"></a>傳回值
 如果成功，會傳回 S_OK;否則，會傳回 HRESULT，表示失敗。 如果 managed 例外狀況發生時，會傳回 0x80020009 (DISP_E_EXCEPTION)。

## <a name="see-also"></a>另請參閱
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>