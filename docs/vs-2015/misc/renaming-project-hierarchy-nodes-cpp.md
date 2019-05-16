---
title: 重新命名專案階層節點 (C++) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686579"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>重新命名專案階層節點 (C++)
您可以使用非受控 HierUtil7 專案架構連線，重新命名專案資料夾階層架構節點C++。 如需詳細資訊，請參閱 < [HierUtil7 範例](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11)。  
  
## <a name="expanding-the-hierarchy-node"></a>展開 [階層] 節點  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>展開 [階層] 節點，並重新命名資料夾  
  
1. 選取 [階層] 節點，使用下列方法：  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` 是對應至該資料夾的階層架構容器和`EXPF_SelectItem`取自<xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS>列舉型別。 `GUID_MacroExplorer` Vsshell.idl 中定義的 GUID 常數，而且是針對範例`rguidPersistenceSlot`函式簽章中`ExtExpand`Hu_node.h 中定義。  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     您可以在資料夾中，找到 Hu_node.h 檔案\<安裝根目錄 > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7:  
  
2. 藉由公佈重新命名 命令使用重新命名資料夾 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` 已<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>指標： `<IVsUIShell>``srpVsUIShell`。 `guiVSStd97` 是的命令群組的唯一識別碼命令`cmdidRename`所屬 Vsshlids.h 中定義。  
  
## <a name="see-also"></a>另請參閱  
 [建立專案類型](../extensibility/internals/creating-project-types.md)   
 [VSSDK 範例](../misc/vssdk-samples.md)