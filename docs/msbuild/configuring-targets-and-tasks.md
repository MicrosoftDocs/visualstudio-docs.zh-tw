---
title: 設定目標和工作 | Microsoft Docs
description: 使用 MSBuild 設定 MSBuild 目標和工作以跨進程執行，讓您可以將不同于您正在執行的內容設為目標。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5548478e5404c69acc92d7ca7dc4deb6a2e29fdf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922536"
---
# <a name="configure-targets-and-tasks"></a>設定目標和工作

您可以設定 MSBuild 目標和工作以跨處理序方式隨 MSBuild 一起執行，如此您就能以與目前執行的內容不同的內容做為目標。 例如，您可以在開發電腦以 64 位元 .NET Framework 4.5 作業系統執行時，以 32 位元 .NET Framework 2.0 應用程式為目標。 您也可以將執行 .NET Framework 4 或以前版本的電腦做為目標。 32 或 64 位元與特定 .NET Framework 版本的組合稱為「目標內容」。

## <a name="installation"></a>安裝

  如果您想要將 MSBuild 與 Visual Studio 分開安裝，可以從 [MSBuild 下載](https://www.microsoft.com/download/details.aspx?id=40760)下載安裝套件。 您也必須安裝要使用的 .NET Framework 版本。

## <a name="targets-and-tasks"></a>目標和工作

 MSBuild 會以跨處理序的方式執行一些建置工作，以鎖定範圍更廣的內容。  例如，32 位元 MSBuild 可在 64 位元處理序中執行建置工作，以鎖定 64 位元電腦。 這是由 `UsingTask` 引數和 `Task` 參數所控制。 .NET Framework 4.5 所安裝的目標會設定這些引數和參數，而且不需進行變更就能為各種目標內容建置應用程式。

 如果您要建立自己的目標內容，則必須適當設定這些引數和參數。 如需範例，請參閱 .NET Framework 4.5 的 *microsoft. 一般 .targets* 檔案和 *Microsoft. common. Tasks* 檔。  如需如何建立可處理多個目標內容的自訂工作，或如何修改現有工作的詳細資訊，請參閱 [如何：設定目標和](../msbuild/how-to-configure-targets-and-tasks.md)工作。

## <a name="see-also"></a>另請參閱

- [多目標](../msbuild/msbuild-multitargeting-overview.md)
