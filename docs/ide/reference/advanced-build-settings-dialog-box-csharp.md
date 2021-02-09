---
title: 進階建置設定對話方塊 (C#)
description: 瞭解如何使用 Visual Studio 來指定專案的 advanced build configuration 屬性。
ms.custom: SEO-VS-2020
ms.date: 08/05/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8569231ee1b9f19752bf58691b41ec74789bb761
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868994"
---
# <a name="advanced-build-settings-dialog-box-c"></a>C # )  ([Advanced Build Settings] 對話方塊

使用 [專案設計工具] 的 [進階建置設定] 對話方塊，以指定專案的進階組建組態屬性。 此對話方塊只適用于 c # 專案。

## <a name="general"></a>一般

下列選項可讓您設定一般進階設定。

**語言版本**

::: moniker range=">=vs-2019"

[/Langversion (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)的連結，其中提供如何根據專案的目標 framework 選擇預設語言版本的相關資訊。

::: moniker-end

::: moniker range="vs-2017"

指定要使用的語言版本。 每個版本的功能集都不同，因此這個選項可用來強制編譯器只允許已實作功能的子集，或只啟用與現有標準相容的功能。

預設值為 c # 7.0。

::: moniker-end

**報告內部編譯器錯誤**

指定是否要向 Microsoft 報告編譯器錯誤。 如果設定為 [提示]\(預設值)，您會在發生內部編譯器錯誤時收到提示，讓您選擇以電子方式將錯誤報告傳送給 Microsoft。 如果設定為 [傳送]，則會自動傳送錯誤報告。 如果設定為 [佇列]，則會將錯誤報告排入佇列。 如果設定為 [無]，則會以編譯器的文字輸出報告錯誤。 如需詳細資訊，請參閱 [/errorreport (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)。

**檢查算術溢位/反向溢位**

指定不在 [checked](/dotnet/csharp/language-reference/keywords/checked) 或 [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) 關鍵字範圍內，且會產生超出該資料類型範圍之值的整數算術陳述式，是否會導致執行階段例外狀況。 如需詳細資訊，請參閱 [/checked (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option)。

**不要參考 mscorlib.dll**

指定是否要將 mscorlib.dll 匯入您的程式，並定義整個 <xref:System> 命名空間。 如果您想要定義或建立自己的 <xref:System> 命名空間和物件，請核取此方塊。 如需詳細資訊，請參閱 [/nostdlib (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option)。

## <a name="output"></a>輸出

下列選項可讓您指定進階輸出選項。

**偵錯資訊**

指定編譯器所產生的偵錯資訊類型。 如需如何設定應用程式效能偵錯的資訊，請參閱[使映像偵錯更容易](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。 此設定具有下列選項：

- 無

   指定不會產生任何偵錯資訊。

- **full**

   允許將偵錯工具附加至執行中的程式。

- **pdbonly**

   讓原始程式碼在偵錯工具中啟動程式時進行偵錯，但只有在將執行中的程式附加到偵錯工具時，才會顯示組譯工具。

- **可擕式**

   產生 .PDB 檔案，這是非平台特定可攜式符號檔，可將主要可執行檔中項目的資訊和其產生方式提供給其他工具 (特別是偵錯工具)。 如需詳細資訊，請參閱 [Portable PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (可攜式 PDB)。

- **嵌入式**

   在組件中內嵌可攜式符號資訊。 不會產生任何外部 .PDB 檔案。

如需詳細資訊，請參閱 [/debug (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)。

**檔案對齊**

指定輸出檔案中區段的大小。 有效值為 **512**、**1024**、**2048**、**4096** 和 **8192**。 這些值是以位元組為單位。 每個區段將會對齊界限，而這個界限就是此值的倍數，會影響輸出檔的大小。 如需詳細資訊，請參閱 [/filealign (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option)。

**程式庫基底位址**

指定載入 DLL 時慣用的基底位址。 DLL 的預設基底位址是由 .NET Framework Common Language Runtime 所設定。 如需詳細資訊，請參閱 [/baseaddress (c # 編譯器選項) ](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option)。

## <a name="see-also"></a>另請參閱

- [C # 編譯器選項](/dotnet/csharp/language-reference/compiler-options/index)
- [專案設計工具、組建頁 (c # ) ](../../ide/reference/build-page-project-designer-csharp.md)
