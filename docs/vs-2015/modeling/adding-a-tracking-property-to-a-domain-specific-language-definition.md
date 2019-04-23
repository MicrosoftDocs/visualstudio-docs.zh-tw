---
title: 特定領域語言定義中加入 追蹤屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6b2b3f87084d4bb1a64f2c43f860c7b8bcaae64c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070481"
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>在網域指定的語言定義中加入追蹤屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何將追蹤屬性新增至網域模型。  
  
 A*追蹤網域*屬性是的屬性，使用者就可以進行更新，但具有預設值的計算方式是使用其他網域屬性或元素的值，這個值。  
  
 比方說，在特定領域語言工具 （DSL 工具） 中，網域類別的屬性具有預設值的計算方式是使用網域類別，而是使用者的名稱，這個值的顯示名稱可以在設計階段變更值，或重設為導出值。  
  
 在本逐步解說中，您可以建立特定領域語言 (DSL) 具有追蹤模型的預設命名空間屬性為基礎的預設值的屬性命名空間。 如需有關追蹤屬性的詳細資訊，請參閱[定義的追蹤屬性](http://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be)。  
  
- 追蹤屬性描述元的 DSL 工具支援。 不過，DSL 設計工具無法用來將追蹤屬性新增至語言中。 因此，您必須新增自訂程式碼來定義和實作的追蹤屬性。  
  
  追蹤屬性有兩種狀態： 追蹤，並更新使用者。 追蹤屬性具有下列功能：  
  
- 在 追蹤狀態，追蹤屬性的值會計算，且會更新為模型變更中的其他屬性的值。  
  
- 在更新使用者狀態的追蹤屬性的值會保留使用者上次設定的屬性值。  
  
- 在 [**屬性**] 視窗中，**重設**命令的屬性是在更新時，才會啟用追蹤屬性依使用者狀態。 **重設**命令會將追蹤屬性來追蹤狀態。  
  
- 在 **屬性**追蹤狀態，其值的追蹤屬性時的視窗會顯示在一般的字型。  
  
- 在 [**屬性**] 視窗中，追蹤屬性在更新時根據使用者狀態，其值會顯示以粗體字。  
  
## <a name="prerequisites"></a>必要條件  
 您可以開始本逐步解說之前，您必須先安裝這些元件：  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../includes/dsl-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>建立 DSL 專案  
 建立您的網域特定語言專案。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1. 建立特定領域語言設計工具的專案。 將它命名為 `TrackingPropertyDSL`。  
  
2. 在  **Domain-specific Language Designer 精靈**，設定下列選項：  
  
    1. 選取  **MinimalLanguage**範本。  
  
    2. 使用預設名稱為特定領域語言， `TrackingPropertyDSL`。  
  
    3. 設定的模型檔案的副檔名`trackingPropertyDsl`。  
  
    4. 使用模型檔案的預設範本圖示。  
  
    5. 設定以產品名稱`Product Name`。  
  
    6. 設定的公司名稱`Company Name`。  
  
    7. 用於在解決方案中，專案的根命名空間中的預設值`CompanyName.ProductName.TrackingPropertyDSL`。  
  
    8. 讓精靈為您的組件建立強式名稱金鑰檔。  
  
    9. 檢閱之方案的詳細資料，然後按**完成**建立 DSL 定義專案。  
  
## <a name="customizing-the-default-dsl-definition"></a>自訂預設的 DSL 定義  
 在本節中，您可以自訂 DSL 定義中包含下列項目：  
  
- 追蹤每個項目之模型的屬性命名空間。  
  
- 模型的每個項目，則為 True 的 IsNamespaceTracking 屬性。 這個屬性會指出追蹤屬性是否會在追蹤狀態或已更新的使用者狀態。  
  
- 模型的預設命名空間屬性。 這個屬性會用於計算的追蹤屬性的命名空間的預設值。  
  
- CustomElements 計算模型的屬性。 這個屬性會指出項目具有自訂命名空間的比例。  
  
#### <a name="to-add-the-domain-properties"></a>若要將網域屬性  
  
1. 在 DSL 設計工具中，以滑鼠右鍵按一下**ExampleModel**網域類別，指向**新增**，然後按一下**DomainProperty**。  
  
    1. 命名新的屬性`DefaultNamespace`。  
  
    2. 在**屬性**視窗中的新的屬性，將**預設值**來`DefaultNamespace`，並設定**型別**到**字串**。  
  
2. 若要**ExampleModel**網域類別中，新增一個名為的網域屬性`CustomElements`。  
  
     在 **屬性**視窗中的新的屬性，將**種類**來**導出**。  
  
3. 若要**ExampleElement**網域類別中，新增一個名為的網域屬性`Namespace`。  
  
     中**屬性**視窗中的新的屬性，將**是可瀏覽**來**False**，並將**種類**來**CustomStorage**.  
  
4. 若要**ExampleElement**網域類別中，新增一個名為的網域屬性`IsNamespaceTracking`。  
  
     中**屬性**視窗中的新的屬性，將**Is Browsable**來**False**，將**預設值**到`true`，並設定**型別**要**布林**。  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>若要更新的圖表項目和 DSL 詳細資料  
  
1. 在 DSL 設計工具中，以滑鼠右鍵按一下**ExampleShape**幾何圖形，指向**新增**，然後按一下**文字裝飾項目**。  
  
    1. 命名新的文字裝飾項目`NamespaceDecorator`。  
  
    2. 在 **屬性**視窗中的文字裝飾項目，將**位置**來**InnerBottomLeft**。  
  
2. 在 DSL 設計工具中，選取 連接的線條**ExampleElement**類別，即可**ExampleShape**圖形。  
  
    1. 在 [ **DSL 詳細資料**視窗中，選取**裝飾項目對應**] 索引標籤。  
  
    2. 在 **裝飾項目**清單中，選取**NamespaceDecorator**，選取其核取方塊，然後在**顯示屬性**清單中，選取**命名空間**.  
  
3. 在 [ **DSL 總管]**，展開**網域類別**資料夾中，以滑鼠右鍵按一下**ExampleElement**節點，然後再按一下**加入新網域類型描述元**.  
  
    1. 依序展開**ExampleElement**節點，然後選取**自訂類型描述元 （網域型別描述項）** 節點。  
  
    2. 在 **屬性**視窗中的網域類型描述元，將**自訂自動程式化**來 **，則為 True**。  
  
4. 在  **DSL Explorer**，選取**Xml 序列化行為**節點。  
  
    1. 在 **屬性**視窗中，將**自訂公佈載入**來 **，則為 True**。  
  
## <a name="transforming-templates"></a>轉換範本  
 既然您已定義的網域類別和屬性，您的 dsl，您可以確認 DSL 定義可被正確轉換為您的專案程式碼重新產生。  
  
#### <a name="to-transform-the-text-templates"></a>若要轉換的文字範本  
  
1. 在 **方案總管**工具列上，按一下**轉換所有範本**。  
  
2. 系統會重新產生的程式碼解決方案，並將儲存 DslDefinition.dsl。 定義檔案的 XML 格式的相關資訊，請參閱[DslDefinition.dsl 檔](../modeling/the-dsldefinition-dsl-file.md)。  
  
## <a name="creating-files-for-custom-code"></a>建立自訂程式碼檔  
 當您轉換所有範本時，系統就會產生 Dsl 和 DslPackage 專案中定義特定領域語言的原始程式碼。 好讓您可以避免干擾產生的文字，請在產生的程式碼檔案不同的檔案中撰寫自訂程式碼。  
  
 您必須提供程式碼維護的值與您的追蹤屬性的狀態。 若要協助您區別自訂程式碼與產生的程式碼，並避免命名衝突的檔案，您的自訂程式碼將檔案放在個別的子資料夾。  
  
#### <a name="to-create-the-code-files"></a>若要建立的程式碼檔案  
  
1. 中**方案總管**，以滑鼠右鍵按一下**DSL**專案，指向**新增**，然後按一下**新資料夾**。 新資料夾命名為`CustomCode`。  
  
2. 以滑鼠右鍵按一下 新**CustomCode**資料夾，指向**新增**，然後按一下**新項目**。  
  
3. 選取**程式碼檔案**範本、 將設定**名稱**來`NamespaceTrackingProperty.cs`，然後按一下**確定**。  
  
     建立並開啟以供編輯 NamespaceTrackingProperty.cs 檔案。  
  
4. 在資料夾中，建立下列的程式碼檔案： `ExampleModel.cs,``HelperClasses.cs`， `Serialization.cs`，和`TypeDescriptor.cs`。  
  
5. 在  **DslPackage**專案中，也建立`CustomCode`資料夾中，並將它加入`Package.cs`程式碼檔案。  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>新增協助程式類別，以支援追蹤屬性  
 HelperClasses.cs 檔案中，新增`TrackingHelper`和`CriticalException`類別，如下所示。 您將會參考這些稍後在本逐步解說中的類別。  
  
#### <a name="to-add-the-helper-classes"></a>若要新增的協助程式類別  
  
1. HelperClasses.cs 檔案中加入下列程式碼。  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        internal static class TrackingHelper  
        {  
            /// <summary>Notify each model element in a collection that a tracked  
            /// property has changed.</summary>  
            /// <param name="store">The store for the model.</param>  
            /// <param name="collection">The collection of model elements that  
            /// contain the tracking property.</param>  
            /// <param name="propertyId">The ID of the tracking property.</param>  
            /// <param name="trackingPropertyId">The ID of the property that  
            /// indicates whether the tracking property is tracking.</param>  
            internal static void UpdateTrackingCollectionProperty(  
                Store store,  
                IEnumerable collection,  
                Guid propertyId,  
                Guid trackingPropertyId)  
            {  
                DomainPropertyInfo propInfo =  
                    store.DomainDataDirectory.GetDomainProperty(propertyId);  
  
                DomainPropertyInfo trackingPropInfo =  
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);  
  
                Debug.Assert(propInfo != null);  
                Debug.Assert(trackingPropInfo != null);  
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),  
                    "Tracking property not specified as a boolean");  
  
                foreach (ModelElement element in collection)  
                {  
                    // If the tracking property is currently tracking, then notify  
                    // it that the tracked property has changed.  
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);  
                    if (isTracking)  
                    {  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
            }  
        }  
  
        /// <summary>Helper class to flag critical exceptions from ones that are  
        /// safe to ignore.</summary>  
        internal static class CriticalException  
        {  
            /// <summary>Gets whether an exception is critical and can not be  
            /// ignored.</summary>  
            /// <param name="ex">The exception to check.</param>  
            /// <returns>True if the exception is critical.</returns>  
            internal static bool IsCriticalException(Exception ex)  
            {  
                if (ex is NullReferenceException  
                    || ex is StackOverflowException  
                    || ex is OutOfMemoryException  
                    || ex is System.Threading.ThreadAbortException)  
                    return true;  
  
                if (ex.InnerException != null)  
                    return IsCriticalException(ex.InnerException);  
  
                return false;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>自訂類型描述元加入自訂程式碼  
 實作`GetCustomProperties`方法的型別描述元`ExampleModel`網域類別。  
  
> [!NOTE]
>  DSL 工具產生的自訂類型描述元的程式碼`ExampleModel`呼叫`GetCustomProperties`; 不過，DSL 工具不會產生程式碼會實作的方法。  
  
 定義這個方法會建立追蹤的追蹤屬性的命名空間的屬性描述元。 此外，針對 [追蹤屬性提供屬性可讓**屬性**才能正確顯示屬性] 視窗。  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>若要修改 ExampleModel 網域類別的型別描述元  
  
1. TypeDescriptor.cs 檔案中加入下列程式碼。  
  
    ```csharp  
    using System;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the custom type descriptor for the ExampleElement domain class, add  
        // the GetCustomProperties method.  
        public partial class ExampleElementTypeDescriptor  
        {  
            /// <summary>Returns the property descriptors for the described  
            /// ExampleElement domain class.</summary>  
            /// <remarks>This method adds the tracking property descriptor.  
            /// </remarks>  
            private PropertyDescriptorCollection GetCustomProperties(  
                Attribute[] attributes)  
            {  
                // Get the default property descriptors from the base class  
                PropertyDescriptorCollection propertyDescriptors =  
                    base.GetProperties(attributes);  
  
                // Get a reference to the model element that is being described.  
                ExampleElement source = this.ModelElement as ExampleElement;  
  
                //Add the descriptor for the tracking property.  
                if (source != null)  
                {  
                    DomainPropertyInfo domainProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.NamespaceDomainPropertyId);  
  
                    DomainPropertyInfo trackingProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);  
  
                    // Define attributes for the tracking property so that the  
                    // Properties window displays the property correctly.  
                    Attribute[] attr = new Attribute[] {  
                        new DisplayNameAttribute("Element Namespace"),  
                        new DescriptionAttribute("The namespace of the element."),  
                        new CategoryAttribute("Tracking Properties"),  
                    };  
  
                    propertyDescriptors.Add(new TrackingPropertyDescriptor(  
                        source, domainProperty, trackingProperty, attr));  
                }  
  
                // Return the property descriptors for this element  
                return propertyDescriptors;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-package"></a>加入自訂程式碼封裝  
 產生的程式碼定義 ExampleElement 網域類別的型別描述提供者不過，您必須新增程式碼，以指示 DSL 以使用此類型描述提供者。  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>若要更新 DSL 封裝，使用您的自訂類型描述元  
  
1. 將下列程式碼新增至 Package.cs 檔。  
  
    ```csharp  
    using System.ComponentModel;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // Override the default Initialize method.  
        internal sealed partial class TrackingPropertyDSLPackage  
        {  
            protected override void Initialize()  
            {  
                // Add the custom type descriptor for the ExampleElement type.  
                TypeDescriptor.AddProvider(  
                    new ExampleElementTypeDescriptionProvider(),  
                    typeof(ExampleElement));  
  
                base.Initialize();  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-model"></a>加入自訂程式碼模型  
 實作`GetCustomElementsValue`方法`ExampleModel`網域類別。  
  
> [!NOTE]
>  DSL 工具產生的程式碼`ExampleModel`呼叫`GetCustomElementsValue`; 不過，DSL 工具不會產生程式碼會實作的方法。  
  
 定義`GetCustomElementsValue`CustomElements 導出屬性的方法提供邏輯`ExampleModel`。 這個方法會計算數目`ExampleElement`具有追蹤使用者已更新的值，並傳回表示這個計數為模型中的總項目所佔百分比的字串屬性的命名空間的網域類別。  
  
 此外，新增`OnDefaultNamespaceChanged`方法，以`ExampleModel`，並覆寫`OnValueChanged`方法`DefaultNamespacePropertyHandler`巢狀類別的`ExampleModel`呼叫`OnDefaultNamespaceChanged`。  
  
 因為 DefaultNamespace 屬性用來計算 追蹤屬性的命名空間`ExampleModel`必須通知所有`ExampleElement`DefaultNamespace 值已變更的網域類別。  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>若要修改的追蹤屬性的屬性處理常式  
  
1. ExampleModel.cs 檔案中加入下列程式碼。  
  
    ```csharp  
    using System.Linq;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        public partial class ExampleModel  
        {  
            public string GetCustomElementsValue()  
            {  
                if (this.Elements.Count == 0) return "0/0";  
  
                int number = this.Elements.Count(e => !e.IsNamespaceTracking);  
                return string.Format("{0}/{1}", number, this.Elements.Count);  
            }  
  
            #region Value changed handler for the tracked property  
  
            // When a tracked property changes, it needs to notify all of the properties  
            // that track it.  
  
            /// <summary>Called by the DefaultNamespace property value handler when the  
            /// DefaultNamespace property changes.</summary>  
            /// <param name="oldValue">The previous value of the property.</param>  
            /// <param name="newValue">The new value of the property.</param>  
            protected virtual void OnDefaultNamespaceChanged(  
                string oldValue, string newValue)  
            {  
                // Use the helper class to notify all of the elements in the model  
                // that the default namespace has changed.  
                TrackingHelper.UpdateTrackingCollectionProperty(  
                    this.Store,  
                    this.Elements,  
                    ExampleElement.NamespaceDomainPropertyId,  
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);  
            }  
  
            // Update the change handler for the DefaultNamespace property.  
            internal sealed partial class DefaultNamespacePropertyHandler  
            {  
                /// <summary>Called when the DefaultNamespace property changes.</summary>  
                /// <param name="element">The model element that has the property that  
                /// changed.</param>  
                /// <param name="oldValue">The previous value of the property.</param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleModel element, string oldValue, string newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
  
                    if (!element.Store.InUndoRedoOrRollback)  
                    {  
                        element.OnDefaultNamespaceChanged(oldValue, newValue);  
                    }  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-tracking-property"></a>加入自訂程式碼的追蹤屬性  
 新增`CalculateNamespace`方法，以`ExampleElement`網域類別。  
  
 定義這個方法提供的 CustomElements 導出屬性的邏輯`ExampleModel`。 這個方法會計算數`ExampleElement`具有追蹤處於 已更新的屬性的命名空間的網域類別的使用者狀態，並傳回表示這個計數為模型中的總項目所佔百分比的字串。  
  
 此外，新增 [儲存體和方法，以取得和設定，命名空間] 自訂儲存屬性的`ExampleElement`網域類別。  
  
> [!NOTE]
>  DSL 工具產生的程式碼`ExampleModel`呼叫 get 和 set 方法; 不過，DSL 工具不會產生實作方法的程式碼。  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>若要加入自訂類型描述元方法  
  
1. NamespaceTrackingProperty.cs 檔案中加入下列程式碼。  
  
    ```csharp  
    using System;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the domain class that has the tracking property, add the caluclation  
        // for when the property is tracking.  
        public partial class ExampleElement  
        {  
            /// <summary>Calculates the actual value of the property when it is  
            /// tracking.</summary>  
            /// <returns>The value of the tracking property when it is  
            /// tracking.</returns>  
            /// <remarks>Making this method virtual allows child classes to modify  
            /// the calculation. This method does not need to perform validation, as  
            /// its caller handles validation prior to calling this method.  
            /// <para>In this case, the tracking value depends on the default namespace  
            /// property of the parent model.</para></remarks>  
            protected virtual string CalculateNamespace()  
            {  
                return this.ExampleModel.DefaultNamespace;  
            }  
  
            #region Tracking property implementation  
  
            // Implement the Namespace domain property of the ExampleElement domain class,  
            // and update the IsNamespaceTracking domain property value handler.  
  
            /// <summary>Storage for the Namespace property.</summary>  
            private string namespaceStorage;  
  
            /// <summary>Gets the value of the Namespace property.</summary>  
            /// <returns>The value of the Namespace property.</returns>  
            private string GetNamespaceValue()  
            {  
                // Only retrieve the tracked value if the store is not in the  
                // middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!loading && this.IsNamespaceTracking)  
                {  
                    try  
                    {  
                        return this.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                        return default(string);  
                    }  
                    catch (Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                        else  
                        {  
                            return default(string);  
                        }  
                    }  
                }  
  
                return namespaceStorage;  
            }  
  
            /// <summary>Sets the value of the Namespace property.</summary>  
            /// <param name="value">The new value for the property.</param>  
            private void SetNamespaceValue(string value)  
            {  
                namespaceStorage = value;  
  
                // Only update the state of the tracking property if the store is  
                // not in the middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!this.Store.InUndoRedoOrRollback && !loading)  
                {  
                    this.IsNamespaceTracking = false;  
                }  
            }  
  
            // Update the default behavior of the ExampleElement.IsNamespaceTracking  
            // domain property value handler.  
            internal sealed partial class IsNamespaceTrackingPropertyHandler  
            {  
                /// <summary>Called after the IsNamespaceTracking property changes.  
                /// </summary>  
                /// <param name="element">The model element that has the property  
                /// that changed.</param>  
                /// <param name="oldValue">The previous value of the property.  
                /// </param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleElement element, Boolean oldValue, Boolean newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
                    if (!element.Store.InUndoRedoOrRollback && newValue)  
                    {  
                        DomainPropertyInfo propInfo =  
                            element.Store.DomainDataDirectory.GetDomainProperty(  
                                ExampleElement.NamespaceDomainPropertyId);  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
  
                /// <summary>Performs the reset operation for the IsNamespaceTracking  
                /// property for a model element.</summary>  
                /// <param name="element">The model element that has the property  
                /// to reset.</param>  
                internal void ResetValue(ExampleElement element)  
                {  
                    object calculatedValue = null;  
  
                    try  
                    {  
                        calculatedValue = element.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                    }  
                    catch (System.Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                    }  
  
                    if ((calculatedValue != null  
                        && object.Equals(element.Namespace, calculatedValue)))  
                    {  
                        element.isNamespaceTrackingPropertyStorage = true;  
                    }  
                }  
  
                /// <summary>Method to set IsNamespaceTracking to false so that this  
                /// instance of this tracking property is not storage-based.  
                /// </summary>  
                /// <param name="element">The element on which to reset the property  
                /// value.</param>  
                internal void PreResetValue(ExampleElement element)  
                {  
                    // Force the IsNamespaceTracking property to false so that the value  
                    // of the Namespace property is retrieved from storage.  
                    element.isNamespaceTrackingPropertyStorage = false;  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-to-support-serialization"></a>加入自訂程式碼，以支援序列化  
 加入以支援 XML 序列化自訂後載入行為的程式碼。  
  
> [!NOTE]
>  DSL 工具產生呼叫的程式碼`OnPostLoadModel`和`OnPostLoadModelAndDiagram`方法; 不過，DSL 工具不會產生程式碼來實作這些方法。  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>加入程式碼以支援自訂的後載入行為  
  
1. Serialization.cs 檔案中加入下列程式碼。  
  
    ```csharp  
    using System;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        #region Helper classes for maintaining state while the store is serializing.  
  
        public abstract partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Reset the tracking state properties to their natural values  
            /// based on comparing storage with calculation.</summary>  
            /// <param name="store">The store that contains this model.</param>  
            internal static void ResetTrackingProperties(Store store)  
            {  
                // Two passes required - one to set all elements to storage-based  
                // then another to set some back to being tracking.  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.PreResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.ResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
            }  
        }  
  
        // Add the pre-reset and reset methods for the model element.  
        public partial class ExampleElement  
        {  
            /// <summary>Calls the pre-reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void PreResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);  
            }  
  
            /// <summary>Calls the reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void ResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);  
            }  
        }  
  
        #endregion  
  
        #region Custom serialization code  
  
        // To the serialization helper for the TrackingPropertyDSL class, add post  
        // load handlers to bind the tracking property to the serialization process.  
        // These handlers manage the tracking states and property values when the  
        // model is serialized and deserialized.  
        public partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Customize model loading.</summary>  
            /// <param name="serializationResult">The serialization result from the  
            /// load operation.</param>  
            /// <param name="partition">The partition in which the new  
            /// instance was created.</param>  
            /// <param name="fileName">The name of the file from which the  
            /// instance was deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.  
            /// </param>  
            private void OnPostLoadModel(  
                SerializationResult serializationResult,  
                Partition partition,  
                string fileName,  
                ExampleModel modelRoot)  
            {  
            }  
  
            /// <summary>Customize model and diagram loading.</summary>  
            /// <param name="serializationResult">Stores serialization result from  
            /// the load operation.</param>  
            /// <param name="modelPartition">Partition in which the new  
            /// instance will be created.</param>  
            /// <param name="modelFileName">Name of the file from which the  
            /// instance will be deserialized.</param>  
            /// <param name="diagramPartition">Partition in which the new  
            /// diagram instance will be created.</param>  
            /// <param name="diagramFileName">Name of the file from which the  
            /// diagram instance will be deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.</param>  
            /// <param name="diagram">The diagram matching the modelRoot.</param>  
            private void OnPostLoadModelAndDiagram(  
                SerializationResult serializationResult,  
                Partition modelPartition,  
                string modelFileName,  
                Partition diagramPartition,  
                string diagramFileName,  
                ExampleModel modelRoot,  
                TrackingPropertyDSLDiagram diagram)  
            {  
                Debug.Assert(modelPartition != null);  
                Debug.Assert(modelPartition.Store != null);  
  
                // Tracking properties need to be set up according to whether the  
                // serialization matches the calculated values.  
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(  
                    modelPartition.Store);  
            }  
        }  
  
        #endregion  
    }  
    ```  
  
## <a name="testing-the-language"></a>測試語言  
 下一個步驟是以建置並執行 DSL 設計工具中的新執行個體[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]，讓您可以驗證是否正常運作的追蹤屬性。  
  
#### <a name="to-exercise-the-language"></a>若要執行的語言  
  
1. 在 [建置] 功能表上，按一下 [重建方案]。  
  
2. 按一下 [偵錯] 功能表上的 [開始偵錯]。  
  
     實驗組建[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]會開啟**偵錯**方案，其中包含空白的測試檔案。  
  
3. 在 **方案總管 中**，按兩下 Test.trackingPropertyDsl 檔案，以在設計工具中開啟它，然後按一下 設計介面。  
  
     請注意，在**屬性**圖表中，視窗**預設命名空間**屬性**DefaultNamespace**，和**自訂項目**屬性是**0/0**。  
  
4. 拖曳**ExampleElement**項目**工具箱**到圖表介面。  
  
5. 中**屬性**視窗中的項目，選取**項目命名空間**屬性，並將值從變更**DefaultNamespace**至**OtherNamespace**。  
  
     請注意，值**項目命名空間**現在會以粗體顯示。  
  
6. 在 **屬性** 視窗中，以滑鼠右鍵按一下**元素命名空間**，然後按一下 **重設**。  
  
     屬性的值會變成**DefaultNamespace**，和一般字型顯示的值。  
  
     以滑鼠右鍵按一下**項目命名空間**一次。 **重設**命令會立即停用，因為屬性目前追蹤狀態。  
  
7. 將另一個**ExampleElement**從**工具箱**圖表介面，並變更其**項目命名空間**至**OtherNamespace**。  
  
8. 按一下設計介面。  
  
     在 **屬性**的值在圖表的視窗**自訂項目**現在**1/2**。  
  
9. 變更**預設命名空間**從圖表**DefaultNamespace**來**NewNamespace**。  
  
     **命名空間**的第一個項目追蹤**預設命名空間**屬性，而**命名空間**第二個項目會保留其使用者已更新值**OtherNamespace**。  
  
10. 儲存方案，然後再關閉 實驗性組建。  
  
## <a name="next-steps"></a>後續步驟  
 如果您想要使用一個以上的追蹤屬性，或在多個 DSL 中實作追蹤屬性，您可以建立文字範本以產生一般的程式碼，以支援每個追蹤的屬性。 如需文字範本的詳細資訊，請參閱[程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)   
 [如何：建立特定領域語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)   
 [逐步解說：自訂特定領域語言定義](../misc/walkthrough-customizing-the-domain-specific-language-definition.md)
