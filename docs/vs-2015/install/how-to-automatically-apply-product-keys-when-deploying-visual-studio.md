---
title: HOW TO：部署 Visual Studio 2015 時，便會自動套用產品金鑰 |Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 11
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 32f8845790168aae784f3659f54c89e000681a15
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53050223"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>HOW TO：在部署 Visual Studio 時自動套用產品金鑰
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 2017 最新文件，請參閱 <<c0> [ 部署 Visual Studio 時會自動套用產品金鑰](/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio)。

您能以程式設計的方式套用您的產品金鑰，作為用來自動化部署 Visual Studio 2015 的一部分指令碼。 產品金鑰能在 Visual Studio 安裝期間或完成安裝後，以程式設計方式設定在裝置上。

## <a name="apply-the-license-during-installation"></a>在安裝期間套用授權
 使用 /ProductKey 參數在進行 Visual Studio 安裝程序時套用產品金鑰。 此安裝程式參數可以搭配 /Silent 參數，以處於已授權狀態的使用者身分來安裝 Visual Studio。 若要使用 /ProductKey 參數，請開啟命令提示字元。 執行安裝程式 (例如，vs_enterprise.exe 或 vs_professional.exe)，然後將 /ProductKey 參數設定為不含破折號的產品金鑰 (25 個字元)：

 這是以 AAAAABBBBBCCCCCDDDDDEEEEEEE 產品金鑰安裝 Visual Studio 2015 Enterprise 的命令範例：

 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`

## <a name="apply-the-license-after-installation"></a>在安裝後套用授權
 您可以在目標電腦上以無訊息模式使用 storePID.exe 公用程式，使用產品金鑰來啟用已安裝的 Visual Studio 版本。 StorePID.exe 是隨 Visual Studio 一起安裝的公用程式，安裝於 **\<磁碟機>:\\\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**。

 藉由使用 System Center 代理程式或提高權限的命令提示字元，後面加上 (包括破折號) 產品金鑰和 Microsoft 產品代碼 (MPC)，以較高的權限執行 StorePID.exe。 請務必包含產品金鑰的破折號！

 `StorePID.exe [product key including the dashes] [MPC]`

 這是以產品金鑰 "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE" 安裝 Visual Studio 2015 Enterprise 的命令列範例，其 MPC 為 07060：

 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`

 下表列出每個 Visual Studio 版本的 MPC 代碼：

|Visual Studio 版本|MPC|
|---------------------------|---------|
|Visual Studio Enterprise 2015|07060|
|Visual Studio Professional 2015|07062|
|Visual Studio Test Professional 2015|07066|
|Visual Studio Ultimate 2013|06181|
|Visual Studio Premium 2013|06191|
|Visual Studio Professional 2013|06177|
|Visual Studio Test Professional 2013|06194|

 如需有關如何取得產品金鑰的詳細資訊，請參閱[How to:找出 Visual Studio 產品金鑰](../install/how-to-locate-the-visual-studio-product-key.md)。

 如果 StorePID.exe 成功套用產品金鑰，會傳回 0。 如果遇到錯誤，則會傳回 1 到 6 的數字。

## <a name="see-also"></a>請參閱
 [安裝 Visual Studio](../install/install-visual-studio-2015.md)