---
title: 為解決方案創建父容器資料夾 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709093"
---
# <a name="create-parent-container-folders-for-solutions"></a>為解決方案建立父容器資料夾
在原始程式碼管理外掛程式 API 版本 1.2 中,用戶可以為解決方案中的所有 Web 專案指定單根根源控制目標。 此單個根稱為超級統一根 (SUR)。

 在原始程式碼管理外掛程式 API 版本 1.1 中,如果使用者向原始程式碼管理添加了多專案解決方案,系統將提示使用者為每個 Web 專案指定一個原始程式碼管理目標。

## <a name="new-capability-flags"></a>新功能旗標
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>新的函式
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 向[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始碼管理添加解決方案時,IDE幾乎總是創建 SUR 資料夾。 具體而言,它在以下情況下這樣做:

- 該專案是檔共用 Web 專案。

- 專案和解決方案檔有不同的驅動器。

- 專案和解決方案檔有不同的共用。

- 項目單獨添加(在原始程式碼管理的解決方案中)。

在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中,建議 SUR 資料夾的名稱與沒有擴展的解決方案名稱相同。 下表總結了兩個版本中的行為。

|功能|原始程式碼管理外掛程式 API 版本 1.1|原始程式碼管理外掛程式 API 版本 1.2|
|-------------| - | - |
|將解決方案加入 SCC|分初始化()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpen專案()|分初始化()<br /><br /> SccGetProjPath()<br /><br /> Scccreate 子專案()<br /><br /> Scccreate 子專案()<br /><br /> SccOpen專案()|
|新增專案到源控制的解決方案|SccGetProjPath()<br /><br /> 開啟項目()|SccGet家長專案路徑()<br /><br /> SccOpen專案()<br /><br />  **註:** 可視化工作室假定解決方案是 SUR 的直接子級。|

## <a name="examples"></a>範例
 下表列出了兩個示例。 在這兩種情況下,都會[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提示使用者在原始程式碼管理下為解決方案指定目標位置,直到*將user_choice*指定為目標。 指定user_choice時,將添加解決方案和兩個專案,而不提示用戶進行原始程式碼管理目標。

|解決方案包含|磁碟位置|資料庫預設結構|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\解決方案\sln1*<br /><br /> *C:[Inetpub]wwwroot_Web1*<br /><br /> \\[伺服器]wwwroot$_Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> 贏1|*C:\解決方案\sln1*<br /><br /> *D:[Inetpub]wwwroot_Web1*<br /><br /> *C:\解決方案\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 無論操作是由於錯誤而取消還是失敗,都會創建 SUR 資料夾和子資料夾。 它們不會在取消或錯誤條件下自動刪除。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如果原始程式管理外掛程式不`SCC_CAP_CREATESUBPROJECT`返回`SCC_CAP_GETPARENTPROJECT`並且功能標誌,則預設為版本 1.1 行為。 此外,用戶[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以選擇通過將以下鍵的值設置為*dword:0000001*來還原到版本 1.1 行為:

 **[HKEY_CURRENT_USER_軟體\微軟[VisualStudio]8.0\源控制]不建立解決方案 RootfolderinSourceControl** = *dword:0000001*

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 版本 1.2 中的新增功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
