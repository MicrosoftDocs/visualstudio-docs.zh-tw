---
title: BscMake 工作 | Microsoft Docs
description: 深入瞭解 BscMake （包裝 Microsoft 流覽資訊維護公用程式工具 bscmake.exe）。 Visual Studio IDE 不再使用 BscMake。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ceda15402b3588e407388d71140b73f571c03b24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964923"
---
# <a name="bscmake-task"></a>BscMake 工作

> [!IMPORTANT]
> Visual Studio IDE 已不再使用 BscMake。 從 Visual Studio 2008 起，瀏覽資訊會自動儲存在 [解決方案] 資料夾的 *.sdf* 檔案中。

 包裝 Microsoft Browse Information Maintenance Utility 工具 (*bscmake.exe*)。  *bscmake.exe* 工具會從編譯期間所建立的來源瀏覽器檔案 (*.sbr*) 建置瀏覽資訊檔 (*.bsc*)。 使用 [物件瀏覽器] 來檢視 *.bsc* 檔案。 如需詳細資訊，請參閱 [BSCMAKE 參考](/cpp/build/reference/bscmake-reference)。

## <a name="parameters"></a>參數

 下表描述 **BscMake** 工作的參數。 大部分的工作參數會對應至命令列選項。

|參數|Description|
|---------------|-----------------|
|**AdditionalOptions**|選擇性的 **字串** 參數。<br /><br /> 選項的清單，如命令列上所指定。 例如，/ \<option1>  / \<option2>  / \<option#> 。 使用這個參數來指定任何其他 **BscMake** 工作參數未表示的選項。<br /><br /> 如需詳細資訊，請參閱 [BSCMAKE 選項](/cpp/build/reference/bscmake-options)中的選項。|
|**OutputFile**|選擇性的 **字串** 參數。<br /><br /> 指定將會覆寫預設輸出檔案名稱的檔案名稱。<br /><br /> 如需詳細資訊，請參閱 [BSCMAKE 選項](/cpp/build/reference/bscmake-options)中的 **/o** 選項。|
|**PreserveSBR**|選擇性的 **布林值** 參數。<br /><br /> 如果是 `true`，會強制執行非累加建置。 無論 *.bsc* 檔案是否存在，都執行完整、非累加建置，並防止 *.sbr* 檔被截斷。<br /><br /> 如需詳細資訊，請參閱 [BSCMAKE 選項](/cpp/build/reference/bscmake-options)中的 **/n** 選項。|
|**來源**|選擇性的 **ITaskItem []** 參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。|
|**SuppressStartupBanner**|選擇性的 **布林值** 參數。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請參閱 [BSCMAKE 選項](/cpp/build/reference/bscmake-options)中的 **/NOLOGO** 選項。|
|**TrackerLogDirectory**|選擇性的 **字串** 參數。<br /><br /> 指定追蹤器記錄檔的目錄。|

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
