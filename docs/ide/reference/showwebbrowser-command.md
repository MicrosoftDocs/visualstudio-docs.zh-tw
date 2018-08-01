---
title: ShowWebBrowser 命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 018d94f2952b8169890377410ff00baf1a80fd41
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176381"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser 命令

顯示您在網頁瀏覽器視窗內指定的 URL (不論是在整合式開發環境 (IDE) 內或 IDE 外部)。

## <a name="syntax"></a>語法

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>引數
 `URL`

 必要。 網站 URL (統一資源定位器)。

## <a name="switches"></a>參數
 /new

 選擇性。 指定頁面會出現在網頁瀏覽器的新執行個體。

 /ext

 選擇性。 指定頁面會出現在 IDE 外面的預設網頁瀏覽器。

## <a name="remarks"></a>備註
 **ShowWebBrowser** 命令的別名是 **navigate** 或 **nav**。

## <a name="example"></a>範例
 下列範例會在 IDE 外面的網頁瀏覽器顯示 MSDN Online 首頁。 如果已經開啟網頁瀏覽器執行個體，便會使用它，否則系統會啟動新的執行個體。

```cmd
>View.ShowWebBrowser http://msdn.microsoft.com /ext
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)