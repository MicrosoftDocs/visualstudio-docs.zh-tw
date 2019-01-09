---
title: XAML 錯誤和警告
ms.date: 03/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7e0a5b4bde839e90bcf852273fa0872b1a5c76f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922608"
---
# <a name="xaml-errors-and-warnings"></a>XAML 錯誤和警告

撰寫 XAML 時，Visual Studio 會在您鍵入的同時分析程式碼。 偵測到錯誤時，程式碼行上會出現曲線。 將滑鼠指標停留在曲線上時，即會顯示錯誤或警告的詳細資訊。 有些錯誤和警告會顯示「快速動作」燈泡，且您可以使用 **Ctrl**+**.** 鍵盤快速鍵以顯示可修正問題的選項。

## <a name="error-types"></a>錯誤類型

系統中的多項工具會在幕後平行分析 XAML。 依據偵測到錯誤的工具來看，XAML 錯誤可以區分為下列三種類型：

|**偵測到錯誤的項目**|**錯誤碼格式**|
| - |-----------------|
|XAML 語言服務 (XAML 編輯器)|XLSxxxx|
|XAML 設計工具|XDGxxxx|
|XAML 編輯後繼續|XECxxxx|

> [!Note]
> 並非所有錯誤或警告都有對應的程式碼。 這種錯誤通常是 XAML 設計工具的錯誤。


## <a name="suppress-xaml-designer-errors"></a>隱藏 XAML 設計工具的錯誤

選取 工具 > 選項，然後選取 文字編輯器 > XAML > 其他，以開啟 選項 對話方塊。

取消選取 [Show errors detected by the XAML designer] (顯示 XAML 設計工具所偵測到的錯誤) 核取方塊。

![隱藏 XAML 設計工具的錯誤](../designers/media/suppress_xaml_designer_errors.png)
