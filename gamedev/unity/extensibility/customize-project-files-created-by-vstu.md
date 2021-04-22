---
title: 自訂 VSTU 所建立的專案檔 | Microsoft Docs
description: '瞭解如何自訂 Visual Studio Tools for Unity (VSTU) 所建立的專案檔。 查看 c # 程式碼範例。'
ms.custom: ''
ms.date: 04/19/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a4a5973863877db2d071f9be8d4689928b21a689
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879313"
---
# <a name="customize-project-files-created-by-vstu"></a>自訂 VSTU 所建立的專案檔
Unity 提供專案檔產生期間的回呼。 在 `OnGeneratedSlnSolution` `OnGeneratedCSProject` 每次重新產生 [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) 專案或方案檔時，使用來執行和方法來修改專案或方案檔。

## <a name="demonstrates"></a>示範
如何自訂 Visual Studio Tools for Unity 所產生的 Visual Studio 專案檔。

## <a name="example"></a>範例

```csharp
using System;
using UnityEditor;
using UnityEngine;

public class ProjectFilePostprocessor : AssetPostprocessor
{
  public static string OnGeneratedSlnSolution(string path, string content)
  {
    // TODO: process solution content
    return content;
  }

  public static string OnGeneratedCSProject(string path, string content)
  {
    // TODO: process project content
    return content;
  }
}
```
