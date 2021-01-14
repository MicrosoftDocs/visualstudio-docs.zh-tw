---
title: 視窗屬性對話方塊、視窗索引標籤 |Microsoft Docs
description: 使用 Windows [屬性] 的 [Windows] 索引標籤，即可顯示與所選取視窗相關的視窗資訊。 請參閱這篇文章以取得這些設定。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03cbcee265855c0e3ee26f75d5937315d64661a2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205394"
---
# <a name="windows-tab-window-properties-dialog-box"></a>視窗屬性對話方塊、視窗索引標籤
使用 [ **Windows** ] 索引標籤，即可顯示與所選取視窗相關之視窗的資訊。 若要顯示 [ [視窗屬性] 對話方塊](../debugger/window-properties-dialog-box.md)，請將焦點移至 [ [Windows View](../debugger/windows-view.md) ] 視窗。 選取樹狀結構中的任何視窗節點，然後從 [ **View** ] 功能表選擇 [**屬性**]。

 [ **Windows** ] 索引標籤上提供下列設定：

|進入|描述|
|-----------|-----------------|
|**下一個視窗**|如果沒有下一個視窗) ，則視窗樹狀檢視中顯示的下一個同級視窗的控制碼 (迭置順序)  ( [無]。 選擇這個專案，以查看下一個視窗的屬性。|
|**上一個視窗**|如果沒有上一個視窗) ，則視窗樹狀檢視中顯示的相同序列 (迭置順序) 的控制碼會 ( [無]。 選擇此專案以查看上一個視窗的屬性。|
|**父視窗**|如果沒有父) ，此視窗的父視窗的控制碼 ( 為 "none"。 選擇此專案以查看父視窗的屬性。|
|**第一個子系**|這個視窗第一個子視窗的控制碼，在視窗樹狀檢視中顯示的順序 (Z 順序)  ( [無]，如果沒有子視窗) 。 選擇這個值以查看第一個子視窗的屬性。|
|**主控視窗**|此視窗擁有者視窗的控制碼。 應用程式的主視窗通常會擁有系統強制回應對話方塊視窗，例如 ( "none" （如果沒有擁有者) ）。 選擇此專案以查看擁有者視窗的屬性。|