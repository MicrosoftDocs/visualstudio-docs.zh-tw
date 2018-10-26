---
title: 逐步解說︰LinqToXmlDataBinding 範例 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c69c69cfed53b0080614984853b3128908c2e89
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893646"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>逐步解說：LinqToXmlDataBinding 範例
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此逐步解說描述 LinqToXmlDataBinding 範例，並說明其兩個主要原始程式檔 (L2DBForm.xaml 和 L2DBForm.xaml.cs) 一些更有趣的內容。  
  
## <a name="prerequisites"></a>必要條件  
 閱讀本逐步解說之前，我們強烈建議您建置並執行 LinqToXmlDataBinding 程式，如[做法：建置並執行 LinqToXmlDataBinding 範例](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)中所述。  
  
## <a name="remarks"></a>備註  
 LinqToXmlDataBinding 程式是由 C# 和 XAML 原始程式檔撰寫的 Windows Presentation Foundation (WPF) 應用程式。 該程式包含定義書籍清單以及讓使用者檢視、加入、刪除與編輯這些項目的內嵌 XML 文件， 並以下列兩個主要原始程式檔組成：  
  
- L2DBForm.xaml 包含適用於主視窗之使用者介面 (UI) 的 XAML 宣告程式碼。 它也包含可定義書籍清單之資料提供者與內嵌 XML 文件的視窗資源區段。  
  
- L2DBForm.xaml.cs 包含與 UI 相關聯的初始化與事件處理方法。  
  
  主視窗分為下列四個 UI 垂直區段：  
  
- **XML**：顯示內嵌書籍清單的 XML 原始檔。  
  
- **書籍清單**：將書籍項目顯示為標準文字，並讓使用者選取和刪除個別的項目。  
  
- **編輯選取的書籍**：可讓使用者編輯與目前所選之書籍項目相關聯的值。  
  
- **加入新的書籍**：可根據使用者輸入的值，建立新的書籍項目。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[L2DBForm.xaml 原始程式碼](../designers/l2dbform-xaml-source-code.md)|包含 L2DBForm.xaml 檔案中，XAML 程式碼的內容和描述。|  
|[L2DBForm.xaml.cs 原始程式碼](../designers/l2dbform-xaml-cs-source-code.md)|包含 L2DBForm.xaml.cs 檔案中，C# 原始程式碼的內容與描述。|  
  
## <a name="see-also"></a>另請參閱  
 [使用 LINQ to XML 的 WPF 資料繫結範例](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [如何：建置並執行 LinqToXmlDataBinding 範例](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)



