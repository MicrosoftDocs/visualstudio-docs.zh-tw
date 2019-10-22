---
title: ShowWebBrowser 命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ecf86bdc7516f05935bd944f23633b3baad2c7c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663514"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser 命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

顯示您在 Web 瀏覽器視窗內指定的 URL (不論是在整合式開發環境 (IDE) 內或 IDE 外部)。

## <a name="syntax"></a>語法

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>引數
 `URL` 必要項。 網站 URL (統一資源定位器)。

## <a name="switches"></a>參數
 /new 選擇性。 指定頁面會出現在網頁瀏覽器的新執行個體。

 /ext 選擇性。 指定頁面會出現在 IDE 外面的預設網頁瀏覽器。

## <a name="remarks"></a>備註
 **ShowWebBrowser** 命令的別名是 **navigate** 或 **nav**。

## <a name="example"></a>範例
 下列範例會在 IDE 外面的網頁瀏覽器顯示 MSDN Online 首頁。 如果已經開啟網頁瀏覽器執行個體，便會使用它，否則系統會啟動新的執行個體。

```
>View.ShowWebBrowser https://msdn.microsoft.com /ext
```

## <a name="see-also"></a>另請參閱
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)[命令視窗](../../ide/reference/command-window.md)[尋找/命令框](../../ide/find-command-box.md) [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)
