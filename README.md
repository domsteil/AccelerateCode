<apex:page docType="html-5.0"
           showHeader="false" sidebar="false"
           standardController="Order__c" extensions="IceCreamAppExtentionController">          
    <apex:stylesheet value="{!URLFOR($Resource.MobileSample_Resources_jQueryMobile, 'jquery.mobile-1.3.0.min.css')}"/>
    <apex:includeScript value="{!URLFOR($Resource.MobileSample_Resources_jQueryMobile, 'jquery-1.9.1.min.js')}"/>
    <apex:includeScript value="{!URLFOR($Resource.MobileSample_Resources_jQueryMobile, 'jquery.mobile-1.3.0.min.js')}"/>
    <apex:includeScript value="{!URLFOR($Resource.MobileSample_Resources_jQueryMobile, 'cordova.force.js')}"/>
    <apex:includeScript value="{!URLFOR($Resource.MobileSample_Resources_jQueryMobile, 'backbone/underscore-1.4.4.min.js')}"/>
    <apex:includeScript value="{!URLFOR($Resource.MobileSample_Resources_jQueryMobile, 'force.entity.js')}"/>
    <apex:includeScript value="{!URLFOR($Resource.MobileSample_Resources_jQueryMobile, 'SObjectData.js')}"/>
    <apex:includeScript value="{!$Resource.StarWebTrader}"/>
    <apex:includeScript value="{!$Resource.StarWebPrintBuilder}"/>
 
    <style>
        .ui-mobile .ui-page-active {
            display: block;
            overflow: visible;
            background: white;
        }
        .ui-btn-up-b:visited, .ui-btn-up-b a.ui-link-inherit{
            color: #7BC043;
            
        }
        .ui-checkbox-on .ui-icon, .ui-radio-on .ui-icon {
            background-color: #7BC043;
        }
        .ui-li, .ui-li.ui-field-contain {
            display: block;
            margin: 0;
            position: relative;
            overflow: visible;
            text-align: left;
            border-width: 0;
            border-top-width: 0px;
            border-bottom-width: 0px;
            text-align: center;
        }
        .ui-li.ui-last-child, .ui-li.ui-field-contain.ui-last-child {
            border-bottom-width: 0px;
            text-align: center;
        }
        .msg-class{
            color:red;
            font-size: 16px;
            font-weight: bold;
            text-align: center;
            
        }
        .canvas{
            //width: 150px;
            //height: 150px;
            //display:none;
            //visibility:hidden;
        }

    </style>
    
    <head>
        
        <title>Orders</title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
        <c:remotetk />
        
       
        <script type="text/javascript">
            //PRINTER STUFF
            var pp = "SP742";
        
            var centerPosition = 0, cursor = 0, i = 0, lineSpace = 0;
            
var canvas = document.createElement("canvas");
canvas.setAttribute("id", "canvasPaper");
canvas.setAttribute("width", "420");
canvas.setAttribute("height", "650");
        //canvas.style.visibility = "hidden"; // to hide the canvas
canvas.style.display = "none"; // to not ruin the layout of the page
    
document.body.appendChild(canvas);
        //document.addEventListener("DOMContentLoaded", onDrawReceipt());
    function DrawCenterText(text) 
{   
    canvas = document.getElementById("canvasPaper");
    if (canvas.getContext) 
    {
        var context = canvas.getContext("2d");
        context.textAlign = "center";
        context.fillText(text, centerPosition, cursor);
        //alert('text is :' + text);
    }
}
        
    function onDrawReceipt(name,scoops,flavors,t1,t2,t3,s1,s2,s3) 
{
    var toppings = '';
    if(t1 == true){
        toppings = '|Peanuts|';
        }
    if(t2 == true){
        toppings = toppings + ' |Oreos|';
        }
    if(t3 == true){
       toppings = toppings + ' |Corn Flakes|';    
        }
    if(s1 == true){
        toppings = '|BC Sauce|';
        }
    if(s2 == true){
        toppings = toppings + ' |Choc Sauce|';
        }
    if(s3 == true){
       toppings = toppings + ' |Str Sauce|'; 
    }
    
    
    
    //switch (document.getElementById("printer").value)
    pp = "SP742";
    switch (pp)
    {
        case "SP742":
            canvas.setAttribute("width", "420");
            canvas.setAttribute("height", "620");
            
            if (canvas.getContext) 
            {
                var context = canvas.getContext("2d");
                context.clearRect(0, 0, canvas.width, canvas.height);
                context.textBaseline = "top";
        
                var font = "26px Myriad Pro";
                //var lalign = "left";
                context.font = font;
                //context.textAlign = lalign;

                lineSpace =  32;
                centerPosition = (canvas.width - 16) / 2;
                cursor = 80;
                cursor += lineSpace;

                DrawCenterText('Name: ' + name);
                cursor += lineSpace;
        
                DrawCenterText('Scoops: '+ scoops); 
                cursor += lineSpace; cursor += lineSpace;
                
                DrawCenterText('Flavor: ' + flavors); 
                cursor += lineSpace; cursor += lineSpace;
                
                DrawCenterText('Toppings: ' + toppings);
                cursor += lineSpace; cursor += lineSpace;
                
                DrawCenterText('Thank you'); 
                cursor += lineSpace; cursor += lineSpace;
                //alert(name + scoops + flavors + toppings);
        
            }
            break;
            
        case "TSP847II" :
            canvas.setAttribute("width", "832");
            canvas.setAttribute("height", "475");
            
            if (canvas.getContext) 
            {
                var context = canvas.getContext("2d");
                context.clearRect(0, 0, canvas.width, canvas.height);
                context.textBaseline = "top";

                var font = "26px Myriad Pro";
                context.font = font;

                lineSpace =  32;
                centerPosition = (canvas.width - 16) / 2;
                cursor = 80;
                cursor += lineSpace;

                DrawCenterText("Thank you for entering to win a $200 Visa gift card using");
                cursor += lineSpace;
                
                DrawCenterText("Star\'s WebPRNT Technology.");
                cursor += lineSpace; cursor += lineSpace;
                
                DrawCenterText("The lucky winner will be notified soon after the event via the email");
                cursor += lineSpace;
        
                DrawCenterText("address listed below.");
                cursor += lineSpace; cursor += lineSpace;
        
                DrawCenterText("Email address: ");
                cursor += lineSpace;
        
                DrawCenterText(document.getElementById("email").value);
                cursor += lineSpace; cursor += lineSpace;
        
                DrawCenterText("Thank you for visiting the Star Micronics Booth!");
                cursor += lineSpace;
        
                font = '24px Myriad Pro';
                context.font = font;
        
                DrawCenterText("For more information visit www.starmicronics.com");  cursor += lineSpace;
                var image = new Image();
        
                image.src = "img/StarLogo1.jpg";
        
                image.onload = function () 
                {
                    context.drawImage(image, -25 * 1.5, 0, image.width * 1.5, image.height * 1.5);
                }

                image.onerror = function () 
                {
                    console.log("Star Logo could not be found.");
                }
            }
            break;
        
        default:
            canvas.setAttribute("width", "576");
            canvas.setAttribute("height", "500");
            
            if (canvas.getContext) 
            {
                var context = canvas.getContext("2d");
                context.clearRect(0, 0, canvas.width, canvas.height);
                context.textBaseline = "top";

                var font = "26px Myriad Pro";
                context.font = font;

                lineSpace =  32;
                centerPosition = (canvas.width - 16) / 2;
                cursor = 80;
                cursor += lineSpace;

                DrawCenterText("Thank you for entering to win a $200 Visa gift");
                cursor += lineSpace;
                
                DrawCenterText("card using Star\'s WebPRNT Technology.");
                cursor += lineSpace; cursor += lineSpace;
                
                DrawCenterText("The lucky winner will be notified soon after the");
                cursor += lineSpace;
                
                DrawCenterText("event via the email address listed below.");
                cursor += lineSpace; cursor += lineSpace;
                
                DrawCenterText("Email address: ");
                cursor += lineSpace;
                
                DrawCenterText(document.getElementById("email").value);
                cursor += lineSpace; cursor += lineSpace;
        
                DrawCenterText("Thank you for visiting the Star Micronics Booth!");
                cursor += lineSpace; cursor += lineSpace;
        
                font = "24px Myriad Pro";
                context.font = font;
        
                DrawCenterText("For more information visit www.starmicronics.com");  cursor += lineSpace;
                var image = new Image();
        
                image.src = "img/StarLogo1.jpg";
        
                image.onload = function () 
                {
                    context.drawImage(image, -25 * 1.5, 0, image.width * 1.5, image.height * 1.5);
                }

                image.onerror = function () 
                {
                    console.log("Star Logo could not be found.");
                }
            }
            break;
    }
}

        function onSendMessage() 
{
    pp = "FVP10";
    switch (pp)
    {
        case "FVP10" :
            var trader = new StarWebPrintTrader({url:"http://10.90.0.111:8001/StarWebPRNT/SendMessage"});
            //alert('ip address sent : http://10.90.3.199:8001/StarWebPRNT/SendMessage');
        break; 
        case "SM-T300i" :
            var trader = new StarWebPrintTrader({url:"http://192.168.1.5:8001/StarWebPRNT/SendMessage"}); //IP address of iOS device running WebPRNT Browser. 
        break;
        case "SP742" :
            var trader = new StarWebPrintTrader({url:"http://192.168.1.30/StarWebPRNT/SendMessage"});
        break;
        case "TSP654II" :
            var trader = new StarWebPrintTrader({url:"http://192.168.1.40/StarWebPRNT/SendMessage"});
        break;
        case "TSP743II" :
            var trader = new StarWebPrintTrader({url:"http://192.168.192.50/StarWebPRNT/SendMessage"});
        break;
        case "TSP847II" :
            var trader = new StarWebPrintTrader({url:"http://192.168.1.60/StarWebPRNT/SendMessage"});
        break;
        case "ASR10" :
            var trader = new StarWebPrintTrader({url:"http://192.168.1.190/StarWebPRNT/SendMessage"});
        break;
    }
    
    trader.onReceive = function (response)
    {
        i++;
        var msg = "Success\n\n";

        msg += "TraderSuccess : [ ' + response.traderSuccess + ' ]\n";
        
        msg += "TraderCode : [' + response.traderCode + ']\n";

        msg += "TraderStatus : [' + response.traderStatus + ']\n";

        if (trader.isCoverOpen            ({traderStatus:response.traderStatus})) {msg += '\tCoverOpen,\n';}
        if (trader.isOffLine              ({traderStatus:response.traderStatus})) {msg += '\tOffLine,\n';}
        if (trader.isCompulsionSwitchClose({traderStatus:response.traderStatus})) {msg += '\tCompulsionSwitchClose,\n';}
        if (trader.isEtbCommandExecute    ({traderStatus:response.traderStatus})) {msg += '\tEtbCommandExecute,\n';}
        if (trader.isHighTemperatureStop  ({traderStatus:response.traderStatus})) {msg += '\tHighTemperatureStop,\n';}
        if (trader.isNonRecoverableError  ({traderStatus:response.traderStatus})) {msg += '\tNonRecoverableError,\n';}
        if (trader.isAutoCutterError      ({traderStatus:response.traderStatus})) {msg += '\tAutoCutterError,\n';}
        if (trader.isBlackMarkError       ({traderStatus:response.traderStatus})) {msg += '\tBlackMarkError,\n';}
        if (trader.isPaperEnd             ({traderStatus:response.traderStatus})) {msg += '\tPaperEnd,\n';}
        if (trader.isPaperNearEnd         ({traderStatus:response.traderStatus})) {msg += '\tPaperNearEnd,\n';}
            
        msg += '\tEtbCounter = ' + trader.extractionEtbCounter({traderStatus:response.traderStatus}).toString() + ' ]\n';

        msg += 'Status : [ ' + response.status + ' ]\n';
        msg += 'ResponseText : [ ' + response.responseText + ' ]\n';
        if (i < 2)
        {
            onSendMessage()
            console.log("running again because value of i is " + i);
        }
        else{ i = 0; }
    }
    trader.onError = function (response) 
    {
        var msg = '- onError -\n\n';
        msg += '\tStatus:' + response.status + '\n';
        msg += '\tResponseText:' + response.responseText;
        //alert(msg);
    }
    try 
    {
        var canvas = document.getElementById('canvasPaper');

        if (canvas.getContext) 
        {
            var context = canvas.getContext('2d');

            var builder = new StarWebPrintBuilder();

            var request = '';
            request += builder.createInitializationElement();
            request += builder.createBitImageElement({context:context, x:0, y:0, width:canvas.width, height:canvas.height});
            request += builder.createCutPaperElement({feed:true, type:"partial"});
            trader.sendMessage({request:request});
        }
    }
    catch (e) 
    {
        //alert(e.message);
    }
}
      
                        
                     /* NOT PRINTER STUFF
                     *************************
                     *****************
                     *********************
                     ************************/
       
           
            var $j = jQuery.noConflict(); 
            var client = new remotetk.Client();
            Force.init(null,null,client,null);
            
            var Orders = new SObjectData();
            Orders.errorHandler = displayError;
            
            $j(document).ready(function() {
                regBtnClickHandlers();
                getAllOrders();
               
                
            });
            
            function getAllOrders() {
                Orders.fetch('soql','SELECT id,name,Scoops__c, Flavors__c, Crushed_Peanuts__c, Oreos__c, Corn_Flakes__c, Burnt_Caramel__c, Chocolate_Syrup__c, Strawberry_Sauce__c from Order__c where Scoops__c !=null LIMIT 3',function() {
                    showOrders(Orders.data());
                });
            }

            function showOrders(records) {    
                $j('#cList').empty();
                $j.each(Orders.data(),
                    function() {
                    var newLi = $j('<li></li>');
                                
                    var newLink = $j('<a id="' +this.Id+ '" data-transition="flip">' + this.name + '</a>');
                    newLink.click(function(e) {
                        e.preventDefault();
                        $j.mobile.showPageLoadingMsg();
                        $j('#scoop').val(Orders.findRecordById([this.id]).Scoops__c);
                        $j('#flavors').val(Orders.findRecordById([this.id]).Flavors__c);
                        $j('#OrderId').val(Orders.findRecordById([this.id]).Id);
                        $j('#error').html('');
                       fsc
                        $j.mobile.changePage('#detailpage', {changeHash: true});
                    });
                    newLi.append(newLink);            
                    newLi.appendTo('#cList');
                  //  x++;
                  });
                
                $j.mobile.hidePageLoadingMsg();
                $j('#cList').listview('refresh');
            }      
        
            function createOrder(e){
                e.preventDefault();
                //console.log('####e: ' + e);
                var cId = $j('#OrderId').val();
                
                var record = Orders.findRecordById(cId);
                if(record == null) { 
                    
                    //new record
                    record = Orders.create();
                   
                    
                }
                 
                
                record.Name= $j('#ordername').val();
                //record.Email__c= $j('#email').val();
                
                record.Scoops__c = $j('.scoopclass:checked').val();
                var flavor ='';
                if($j('.flavorclass1:checked').val())
                    flavor  = $j('.flavorclass1:checked').val() + ';';
                if($j('.flavorclass2:checked').val())    
                    flavor  = flavor  + $j('.flavorclass2:checked').val() + ';';
                if($j('.flavorclass3:checked').val())
                    flavor = flavor + $j('.flavorclass3:checked').val() + ';';
                if($j('.flavorclass4:checked').val())
                    flavor =  flavor + $j('.flavorclass4:checked').val()  + ';';
                
                record.Flavors__c =flavor;
                
                var check1 = $j('.toppingclass1:checked').val();
                if($j('.toppingclass1:checked').val()){
                    record.Crushed_Peanuts__c=true;
                }
                if($j('.toppingclass2:checked').val()){
                    record.Oreos__c=true;
                }
                if($j('.toppingclass3:checked').val()){
                    record.Corn_Flakes__c=true;
                }
                
                var check2 = $j('.sauceclass1:checked').val();
                if($j('.sauceclass1:checked').val()){
                   record.Burnt_Caramel__c=true;
                }
                if($j('.sauceclass2:checked').val()){
                    record.Chocolate_Syrup__c=true;
                }
                if($j('.sauceclass3:checked').val()){
                    record.Strawberry_Sauce__c=true;
                }
                
                
                parseObjectinfo(record);
                
                Orders.sync(record,successCallback);
                
                $j('#ordername').val('');
                //$j('#email').val('');
                $j('.scoopclass').attr("checked",false).checkboxradio("refresh");
                $j('.flavorclass1').attr("checked",false).checkboxradio("refresh");
                $j('.flavorclass2').attr("checked",false).checkboxradio("refresh");
                $j('.flavorclass3').attr("checked",false).checkboxradio("refresh");
                $j('.flavorclass4').attr("checked",false).checkboxradio("refresh");
                $j('.sauceclass1').attr("checked",false).checkboxradio("refresh");
                $j('.sauceclass2:checked').attr("checked",false).checkboxradio("refresh");
                $j('.sauceclass3:checked').attr("checked",false).checkboxradio("refresh");
                $j('.toppingclass1').attr("checked",false).checkboxradio("refresh");
                $j('.toppingclass2:checked').attr("checked",false).checkboxradio("refresh");
                $j('.toppingclass3:checked').attr("checked",false).checkboxradio("refresh");
               
                Visualforce.remoting.Manager.invokeAction(
                    '{!$RemoteAction.IceCreamAppExtentionController.getOrderId}', 
                    
                    function(result, event){;
                        if(event.status){
                            console.log('@@@ result : '+result);
                            JSONOrderResult = JSON.stringify(result);
                            
                            //alert(JSONOrderResult);
                             var OrderResult = '<h2 style="color:#7BC043;font-size:18px;">Voila! Your frozen custard is now configured. You can pick up your delightful treat in 5 minutes at the frozen custard booth. Thank you for experiencing the power of Apttus CPQ on the Salesforce1 platform. We hope you enjoy Accelerate 2015!</h2><br/><br/><h2 style="color:#7BC043;font-size:18px;">Order Summary</h2><table style="color:#7BC043; background-color: white;" data-role="table" data-mode="columntoggle" class="ui-responsive ui-shadow" id="myTable">';
                                 var json = $j.parseJSON(JSONOrderResult);
                                		$j(json).each(function(i,val){
                                			$j.each(val,function(k,v){
                                				  console.log(k+" : "+ v);  
                                				  if(!v){
                                				      
                                				  }else{
                                				     
                                				     if(k == 'Id'){
                                				         
                                				     }else{
                                    				      if(typeof v =='boolean')
                                    				        v= 'Yes';
                                    				      if(k =='Name')
                                    				        k= 'Name';
                                    				      if(k =='Flavors__c')
                                    				        v = v.split(";").join(", ");
                                    				        k = k.split("__c").join(" ");
                                                            k = k.split("_").join("");
                                                           
                                    				        OrderResult = OrderResult + '<tr><td style="color:#7BC043;width:200px;font-size:12px;">' + k +'</td><td style="color:#7BC043;width:200px;font-size:12px;">' + v +'</td></tr>';	
                                				      }
                                		          }
                                		});
                                		});
                           
                                    OrderResult = OrderResult + '</table>';
                                    //alert(OrderResult);
                                    $j(".divOrderResult").append(OrderResult);
                           
                                    
                        } else if (event.type === 'exception'){
                        console.log(result);
                       }
                    });
                 /*   
                 Visualforce.remoting.Manager.invokeAction(
                    '{!$RemoteAction.IceCreamAppExtentionController.getAttachment}', 
                    
                    function(result, event){;
                        if(event.status){
                            console.log('@@@ result : '+result);
                            var attachmentId = result;
                            
                            //attchurl = 'https://c.na16.content.force.com/servlet/servlet.FileDownload?file=' + attachmentId;
                            attchurl = 'https://c.na16.content.force.com/servlet/servlet.ImageServer?id=' + attachmentId + '&oid=00Dj0000001tDvL';
                            gcp(attchurl);
                        } else if (event.type === 'exception'){
                        console.log(result);
                       }
                    }); */
                    
                
                 
                 $j.mobile.showPageLoadingMsg();
                
            }
        
            function parseObjectinfo(record){
              var name = record.Name;
                //alert(name);
              var scoops = record.Scoops__c;
                //alert(scoops);
              var flavors = record.Flavors__c;
                // alert(flavors);
              var s1 = record.Burnt_Caramel__c;
              var s2 = record.Chocolate_Syrup__c;
              var s3 = record.Strawberry_Sauce__c;
              var t1 = record.Crushed_Peanuts__c;
              var t2 = record.Oreos__c;
              var t3 = record.Corn_Flakes__c;
                
               onDrawReceipt(name,scoops,flavors,s1,s2,s3,t1,t2,t3);
              onSendMessage();
                
             }
        
            function deleteOrder(e){
                e.preventDefault();
                Orders.remove(Orders.findIndexById($j('#OrderId').val()),successCallback);
            }
            
            function successCallback(r){
                getAllOrders();
                $j.mobile.changePage('#ordersuccess', {changeHash: true,transition: "flip"});
            }
        
            function displayError(e){
                console.log(e);
                $j('#error').html(e[0].message);
            }
        
            function regBtnClickHandlers() {
                $j('#add').click(function(e) {
                    e.preventDefault();
                    $j.mobile.showPageLoadingMsg();
                    $j('#ordername').val('');
                    $j('#email').val('');
                    //$j('#toppingclass1').val('');
                    // $j('#toppingclass2').val('');
                    //  $j('#toppingclass3').val('');
                    //   $j('#toppingclass4').val('');
                    //    $j('#flavorclass').attr("checked",false).checkboxradio("refresh");
                     //    $j('#scoopclass').attr("checked",false).checkboxradio("refresh");
                    $j('#error').html('');
                    $j('#OrderId').val('');
                    //$j.mobile.changePage('#detailpage', {changeHash: true});
                   // $j.mobile.hidePageLoadingMsg();            
                });
        
                $j('#placeorder').click(function(e) {
                   createOrder(e);
                });
        
                $j('#delete').click(function(e) {
                   deleteOrder(e);
                });
            }
            function checkName(selection){
            
                if( $j('#ordername').val()=='' || $j('#email').val()==''){
                    
                    $j('.ordermsgclass').show();
                    
                }
                if( $j('#ordername').val()!='' && $j('#email').val()!=''){
                    //add name and email here
                    $j('.ordermsgclass').hide();
                    $j('.scoopselectmsgclass').hide();
                    $j('.toppingselectmsgclass    ').hide();
                    if(selection=='scoopselection')
                        //here to add
                        $j.mobile.changePage('#scoopselection', {changeHash: true,transition: "flip"});
                        
                    if(selection=='flavorsselection'){
                        
                        if(!$j('.scoopclass:checked').val())
                              $j('.scoopselectmsgclass').show();
                        else{
                              //add here
                              $j.mobile.changePage('#flavorsselection', {changeHash: true,transition: "flip"});
                        }
                    }
                    
                    if(selection=='toppingselection'){

                        if((!$j('.sauceclass1:checked').val()) && (!$j('.sauceclass2:checked').val()) && (!$j('.sauceclass3:checked').val()))
                              $j('.toppingselectmsgclass    ').show();
                        else{
                            //add here
                              $j.mobile.changePage('#toppingselection', {changeHash: true,transition: "flip"});
                    
                        }
                   }
               }   
            
            }
            var counter=0;
            function checkmax(){
            
                if($j('.flavorclass1:checked').val())
                    counter++;
                if($j('.flavorclass2:checked').val())
                    counter++;
                if($j('.flavorclass3:checked').val())
                    counter++;
                if($j('.flavorclass4:checked').val())
                    counter++;
                if(counter==0)
                     $j('.flavormsgclassnone').show(); 
                else {             
                
                    if($j('.scoopclass:checked').val()=='One Scoop'){
                                   
                         if(counter>1){
                             $j('.flavormsgclassone').show();
                         }else{
                             $j('.flavormsgclassone').hide();
                             $j('.flavormsgclasstwo').hide();
                             $j('.flavormsgclassnone').hide(); 
                             
                             $j.mobile.changePage('#sauceselection', {changeHash: true,transition: "flip"});
                         }    
                         
                    }    
                    if($j('.scoopclass:checked').val()=='Two Scoop'){
                         console.log('counter : ' + counter ); 
                         if(counter>2){
                             $j('.flavormsgclasstwo').show(); 
                             
                         }else{
                             $j('.flavormsgclassone').hide();
                             $j('.flavormsgclasstwo').hide();
                             $j('.flavormsgclassnone').hide();
                             $j.mobile.changePage('#sauceselection', {changeHash: true,transition: "flip"});
                         } 
                    }   
                    counter=0;
                }    
            }
            var counter=0;
            function checkmax2(){
            
                if($j('.flavorclass1:checked').val())
                    counter++;
                if($j('.flavorclass2:checked').val())
                    counter++;
                if($j('.flavorclass3:checked').val())
                    counter++;
                if($j('.flavorclass4:checked').val())
                    counter++;
                if(counter==0)
                     $j('.flavormsgclassnone').show(); 
                else {             
                
                    if($j('.scoopclass:checked').val()=='One Scoop'){
                                   
                         if(counter>1){
                             $j('.flavormsgclassone').show();
                         }else{
                             $j('.flavormsgclassone').hide();
                             $j('.flavormsgclasstwo').hide();
                             $j('.flavormsgclassnone').hide(); 
                             
                             $j.mobile.changePage('#toppingselection', {changeHash: true,transition: "flip"});
                         }    
                         
                    }    
                    if($j('.scoopclass:checked').val()=='Two Scoop'){
                         console.log('counter : ' + counter ); 
                         if(counter>2){
                             $j('.flavormsgclasstwo').show(); 
                             
                         }else{
                             $j('.flavormsgclassone').hide();
                             $j('.flavormsgclasstwo').hide();
                             $j('.flavormsgclassnone').hide();
                             $j.mobile.changePage('#toppingselection', {changeHash: true,transition: "flip"});
                         } 
                    }   
                    counter=0;
                }    
            }
        
            $j(document).on('click', '.clearmsgclass', function(){
             
             //function clearmsg(){
            
                $j('#ordername').val('');
                $j('#email').val('');
                $j('.ordermsgclass').hide();
                $j('.scoopselectmsgclass').hide();
                $j('.toppingselectmsgclass').hide();
                if($j('.scoopclass:checked').val())
                    $j('.scoopclass').attr("checked",false).checkboxradio("refresh");
                if($j('.flavorclass1:checked').val())
                    $j('.flavorclass1').attr("checked",false).checkboxradio("refresh");
                if($j('.flavorclass2:checked').val())
                    $j('.flavorclass2').attr("checked",false).checkboxradio("refresh");
                if($j('.flavorclass3:checked').val())
                    $j('.flavorclass3').attr("checked",false).checkboxradio("refresh");
                if($j('.flavorclass4:checked').val())
                    $j('.flavorclass4').attr("checked",false).checkboxradio("refresh");
                if($j('.sauceclass1:checked').val())    
                    $j('.sauceclass1').attr("checked",false).checkboxradio("refresh");
                if($j('.sauceclass2:checked').val())      
                    $j('.sauceclass2:checked').attr("checked",false).checkboxradio("refresh");
                if($j('.sauceclass3:checked').val())     
                    $j('.sauceclass3:checked').attr("checked",false).checkboxradio("refresh");
                if($j('.toppingclass1:checked').val())    
                    $j('.toppingclass1').attr("checked",false).checkboxradio("refresh");
                if($j('.toppingclass2:checked').val())      
                    $j('.toppingclass2:checked').attr("checked",false).checkboxradio("refresh");
                if($j('.toppingclass3:checked').val())     
                    $j('.toppingclass3:checked').attr("checked",false).checkboxradio("refresh");
              
                
                $j.mobile.changePage('#orderpage', {changeHash: true,transition: "flip"});
                
                location.reload();
                
            });
            
            function hideallmsgs(){
                
                $j('.ordermsgclass').hide();
                $j('.scoopselectmsgclass').hide();
                $j('.toppingselectmsgclass').hide();
                $j('.flavormsgclassone').hide();
                $j('.flavormsgclasstwo').hide();
                $j('.flavormsgclassnone').hide();     
                
            }
            function checkscoop(){
                
                if(!$j('.scoopclass:checked').val())
                     $j('.scoopselectmsgclass').show();
                else
                    $j.mobile.changePage('#flavorsselection', {changeHash: true,transition: "flip"});        
            }

           
            function flavourimagedisplay() {
                
              
               
               if($j('.flavorclass1:checked').val())
                    $j('.checkbox-flavor-one-image').show();
                else
                    $j('.checkbox-flavor-one-image').hide();
                    
                if($j('.flavorclass2:checked').val())
                    $j('.checkbox-flavor-two-image').show();
                else
                    $j('.checkbox-flavor-two-image').hide();
                    
                if($j('.flavorclass3:checked').val())
                    $j('.checkbox-flavor-three-image').show();
                else
                    $j('.checkbox-flavor-three-image').hide();
                    
                if($j('.flavorclass4:checked').val())
                    $j('.checkbox-flavor-four-image').show();
                else
                    $j('.checkbox-flavor-four-image').hide();
                    
             
                
            }
            
            function toppingimagedisplay() {
                
                if($j('.toppingclass1:checked').val())
                     $j('.checkbox-topping-one-image').show();
                else
                     $j('.checkbox-topping-one-image').hide();
                
                if($j('.toppingclass2:checked').val())
                    $j('.checkbox-topping-two-image').show();
                else
                    $j('.checkbox-topping-two-image').hide();
                    
                if($j('.toppingclass3:checked').val())
                    $j('.checkbox-topping-three-image').show();
                else
                    $j('.checkbox-topping-three-image').hide();
                    
                        
              } 
        
        
        		function sauceimagedisplay() {
                
                if($j('.sauceclass1:checked').val())
                     $j('.checkbox-sauce-one-image').show();
                else
                     $j('.checkbox-sauce-one-image').hide();
                
                if($j('.sauceclass2:checked').val())
                    $j('.checkbox-sauce-two-image').show();
                else
                    $j('.checkbox-sauce-two-image').hide();
                    
                if($j('.sauceclass3:checked').val())
                    $j('.checkbox-sauce-three-image').show();
                else
                    $j('.checkbox-sauce-three-image').hide();
                    
               }
            
        </script>    
    </head>
 <form>   
    <body>
     
        <div data-role="page" data-theme="b" id="homepage">                
          
            <div data-theme="b"  align="center">
                <img src="{!URLFOR($Resource.frozenc)}" alt="Smiley face" />
                <br/>
                 
                <ul style="font-size: 18px; color:#7BC043; list-style-type: none; list-style-position:inside; margin:2; padding:0; ">
                    <li><strong>Welcome to Accelerate 2015!</strong></li>
                    <li>Experience the power of Apttus CPQ on the Salesforce 1 Platform, where configuration doesn’t have to be all work. Click order to start configuring your very own frozen custard!</li>
                </ul>
                <ul style="font-size: 18px; color:#7BC043; list-style-type: none; list-style-position:inside; margin:2; padding:0; ">
                
                    <li><strong>Dates and Times for Frozen Kuhsterd</strong></li>
                    <li>Wednesday, April 8</li>
                    <li>Ready to serve 11:45AM – 12:45PM (Lunch)</li>
                    <li>4:45 PM – 5:00 PM (Break)</li>
                    <br/>
                    <li>Thursday, April 9</li>
                    <li>Ready to serve 12:15 – 1:15 PM (Lunch)</li>
                    <li>3:00 – 3:30 PM (Break)</li>
                    <li>6:30 PM – 7:30 PM (Happy Hour)</li>

                </ul>
                    <a href='javascript:void(0);' align="center" id="homepageId" class='ui-btn-center clearmsgclass' data-role="button" data-direction="reverse" data-transition="flip"  style="background:#7bc043; color:white;">Order</a>
            </div>
           
            
        </div>
        
        <div data-role="page" data-theme="b" id="ordersuccess"  align="center">
            <div>
                   <img src="{!URLFOR($Resource.Apttussf)}" alt="Smiley face" />
                <br/>
                <br/>
                   <img src="{!URLFOR($Resource.frozen)}" alt="Smiley face" />
                <br/>
                <br/>
            </div>
             <a href='#homepage' id="homepageId" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="flip" style="background:#7bc043; color:white;">Home</a>
             <br/>
             <br/>
            <div class="divOrderResult"></div>
                    
            
             
         </div> 
      
        <div data-role="page" data-theme="b" id="orderpage">
            <div data-role="fieldcontain">
                   <div data-theme="b"  align="center">
                       <img src="{!URLFOR($Resource.Apttussf)}" alt="Smiley face" />
                       
                       <div style="background:white; color:#7BC043; text-align: center;"><h3 style="font-size: 18px;">You can now begin building your delectable frozen custard by entering your first and last name below!</h3>
                       </div>
                           
                   </div>
                   <div style="padding:10px;" data-theme="b" align="center">
                   
                   <input  name="ordername" id="ordername" placeholder="Please enter your first and last name here." required="true" style="background:white; color:black;"/>
                   <input id="OrderId" name="OrderId" type="hidden" />
                   </div>
                   <div id="ordermsg" style="display:none;" class="ordermsgclass msg-class"> Please enter your order name.</div>
                   <div id="scoopselectmsg" style="display:none;" class="scoopselectmsgclass msg-class"> Please select scoop first.</div>
                   <div id="toppingselectmsg" style="display:none;" class="toppingselectmsgclass msg-class"> Please select flavor first.</div>
            </div>        
            <ul data-role="listview" data-theme="b" data-dividertheme="b">
                    <li style="background:white; color:#7BC043;border-top-width: 1px;"><a href="javascript:void(0);" onclick="checkName('scoopselection');" style="background:#7bc043; color:white;">Scoops</a></li>
                    <li style="background:white; color:#7BC043;border-top-width: 1px;"><a href="javascript:void(0);" onclick="checkName('flavorsselection');" style="background:#7bc043; color:white;">Flavors</a></li>
                    <li style="background:white; color:#7BC043;border-top-width: 1px;"><a href="javascript:void(0);" onclick="checkName('sauceselection');" style="background:#7bc043; color:white;">Sauces</a></li>
                    <li style="background:white; color:#7BC043;border-top-width: 1px;border-bottom-width: 1px;"><a href="javascript:void(0);" onclick="checkName('toppingselection');" style="background:#7bc043; color:white;">Toppings</a></li>
                   <div data-theme="b"  align="center">
                       <br/>             
                       <br/>
                       <img src="{!URLFOR($Resource.frozen)}" alt="Smiley face" />
                   </div>
                <br/>
            </ul>
            <a href='#homepage'  id="homepageId" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="flip" style="background:#7bc043; color:white;">Home</a>
            
        </div>
      
          
        <div data-role="page" data-theme="b" id="scoopselection">
            <div data-theme="b"  align="center">
               <img src="{!URLFOR($Resource.Apttussf)}" alt="Smiley face" />
           </div>
            
            <ul data-role="listview">
                    <li style="background:white; color:#7BC043; text-align: center;"><h3 style="font-size: 18px;">How many scoops would you like?</h3></li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >                              
                            
                                
                            
                            <input type="radio" name="radio-scoop" id="radio-scoop-one" value="One Scoop" class="scoopclass" style="background:white; color:#7BC043;"/>
                            <label  for="radio-scoop-one" style="background:#7bc043; color:white;text-align: center;">One Scoop</label>
                            
                        </fieldset>
                    
                    </li>
                 
                 
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="radio" name="radio-scoop" id="radio-scoop-two" value="Two Scoop" class="scoopclass" style="background:white; color:#7BC043;"/>
                            <label  for="radio-scoop-two" style="background:#7bc043; color:white;text-align: center;">Two Scoop</label>
                        </fieldset>
                    
                    </li>
            </ul>
            <a href='javascript:void(0);' id="scoopselectionId" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="flip" style="background:#7bc043; color:white;" onclick="checkscoop();">Next</a>
            <a href='#orderpage' id="backtoorderId" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="flip" style="background:#7bc043; color:white;" onclick="hideallmsgs();">Back</a>
            <div id="scoopselectmsgonscoop" style="display:none;" class="scoopselectmsgclass msg-class"> Please select how many scoops you would like.</div>
            <div data-theme="b"  align="center">
                <br/>
                <br/>
                <br/>
                <br/>
                <br/>
            
               <img src="{!URLFOR($Resource.frozen)}" alt="Smiley face" />
           </div>
        </div>
        
        <div data-role="page" data-theme="b" id="flavorsselection">   
            <div data-theme="b"  align="center">
               <img src="{!URLFOR($Resource.Apttussf)}" alt="Smiley face" />
                
           </div>   
            
            <ul data-role="listview">
                <li style="background:white; color:#7BC043; text-align: center;"><h3 style="font-size: 18px;">What flavors would you like?</h3></li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-flavor" id="checkbox-flavor-one" value="Coffee" class="flavorclass1"  style="background:white; color:#7BC043;" onclick="flavourimagedisplay();"/>
                            <label  for="checkbox-flavor-one" style="background:#7bc043; color:white;text-align: center;">Coffee</label>
                        </fieldset>
                    
                    </li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-flavor" id="checkbox-flavor-two" value="Mint Green" class="flavorclass2"  style="background:white; color:#7BC043;" onclick="flavourimagedisplay();" />
                            <label  for="checkbox-flavor-two" style="background:#7bc043; color:white;text-align: center;">Mint Green</label>
                        </fieldset>
                    
                    </li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-flavor" id="checkbox-flavor-three" value="Blue Velvet" class="flavorclass3"  style="background:white; color:#7BC043;" onclick="flavourimagedisplay();" />
                            <label  for="checkbox-flavor-three" style="background:#7bc043; color:white;text-align: center;">Blue Velvet</label>
                        </fieldset>
                    
                    </li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-flavor" id="checkbox-flavor-four" value="Guittard Chocolate" class="flavorclass4"  style="background:white; color:#7BC043;" onclick="flavourimagedisplay();" />
                            <label  for="checkbox-flavor-four" style="background:#7bc043; color:white;text-align: center;">Guittard Chocolate</label>
                        </fieldset>
                    
                    </li>
                  
            </ul>
            <a href='javascript:void(0);' id="flavorsselectionId" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="flip" onclick="checkmax();" style="background:#7bc043; color:white;">Next</a>
            <a href='#scoopselection' id="backtoscoopId" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="flip" style="background:#7bc043; color:white;" onclick="hideallmsgs();">Back</a>
            <div id="ordermsg" style="display:none;" class="flavormsgclassone msg-class"> You can only select one flavor.</div>
            <div id="ordermsg" style="display:none;" class="flavormsgclasstwo msg-class"> You can only select two flavors.</div>  
            <div id="ordermsg" style="display:none;" class="flavormsgclassnone msg-class"> Please select atleast one flavor.</div>  
            <div data-theme="b"  align="center">
               <img src="{!URLFOR($Resource.cafe)}" alt="Smiley face" class="checkbox-flavor-one-image" style="display:none;"/>
               <img src="{!URLFOR($Resource.green)}" alt="Smiley face" class="checkbox-flavor-two-image" style="display:none;"/>
               <img src="{!URLFOR($Resource.blue)}" alt="Smiley face" class="checkbox-flavor-three-image" style="display:none;"/>
               <img src="{!URLFOR($Resource.chocolate)}" alt="Smiley face" class="checkbox-flavor-four-image" style="display:none;"/>
               
           </div>
        </div>
        
        <div data-role="page" data-theme="b" id="sauceselection">   
            <div data-theme="b"  align="center">
                
               <img src="{!URLFOR($Resource.Apttussf)}" alt="Smiley face" />
                
                
           </div>   
            
                                   
            <ul data-role="listview">
                    <li style="background:white; color:#7BC043; text-align: center;"><h3 style="font-size: 18px;">Would you like any sauces?</h3></li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-h-6a" id="checkbox-sauce-one" class="sauceclass1" onclick="sauceimagedisplay();"/>
                            <label  for="checkbox-sauce-one" style="background:#7bc043; color:white;text-align: center;">Burnt Caramel</label>
                        </fieldset>
                    
                    </li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-h-6a" id="checkbox-sauce-two" class="sauceclass2" onclick="sauceimagedisplay();"/>
                            <label  for="checkbox-sauce-two" style="background:#7bc043; color:white;text-align: center;">Chocolate Sauce</label>
                        </fieldset>
                    
                    </li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-h-6a" id="checkbox-sauce-three" class="sauceclass3" onclick="sauceimagedisplay();"/>
                            <label  for="checkbox-sauce-three" style="background:#7bc043; color:white;text-align: center;">Strawberry Sauce</label>
                        </fieldset>
                    
                    </li>
            </ul>
            
            <a href='javascript:void(0);' id="flavorsselectionId" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="flip" onclick="checkmax2();" style="background:#7bc043; color:white;">Next</a>
            <a href='#flavorsselection' id="backtoflavorId" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="flip" style="background:#7bc043; color:white;" onclick="hideallmsgs();">Back</a>
            <div data-theme="b"  align="center">
                <br/>
            
           </div>
            <br/>
            <br/>
            <br/>
            <br/>
            
          <div  data-theme="b" align="center">
             <img src="{!URLFOR($Resource.caramel)}" alt="Smiley face" class="checkbox-sauce-one-image" style="display:none;"/>
               <img src="{!URLFOR($Resource.chocosauce)}" alt="Smiley face" class="checkbox-sauce-two-image" style="display:none;"/>
                <img src="{!URLFOR($Resource.straw)}" alt="Smiley face" class="checkbox-sauce-three-image" style="display:none;"/>
            </div>
        </div>  
          
            
        
        <div data-role="page" data-theme="b" id="toppingselection">   
            <div data-theme="b"  align="center">
               <img src="{!URLFOR($Resource.Apttussf)}" alt="Smiley face" />
                
           </div>   
            <ul data-role="listview">
                    <li style="background:white; color:#7BC043; text-align: center;"><h3 style= "font-size: 18px;">Would you like any toppings?</h3></li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-h-6a" id="checkbox-topping-one" class="toppingclass1" onclick="toppingimagedisplay();"/>
                            <label  for="checkbox-topping-one" style="background:#7bc043; color:white;text-align: center;">Crushed Peanuts</label>
                        </fieldset>
                    
                    </li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-h-6a" id="checkbox-topping-two" class="toppingclass2" onclick="toppingimagedisplay();"/>
                            <label  for="checkbox-topping-two" style="background:#7bc043; color:white;text-align: center;">Oreos</label>
                        </fieldset>
                    
                    </li>
                    <li style="background:white; color:#7BC043;">
                    
                        <fieldset class="myhover" data-role="controlgroup" data-iconpos="right" >
                            <input type="checkbox" name="checkbox-h-6a" id="checkbox-topping-three" class="toppingclass3" onclick="toppingimagedisplay();"/>
                            <label  for="checkbox-topping-three" style="background:#7bc043; color:white;text-align: center;">Corn Flakes</label>
                        </fieldset>
                    
                    </li>
            </ul>
            <input type="hidden" id="OrderId" />          
            <a id="placeorder" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="slidefade" style="background:#7bc043; color:white; ">Order</a>
            
            <a href='#sauceselection' id="backtosauceId" class='ui-btn-center' data-role="button" data-direction="reverse" data-transition="flip" style="background:#7bc043; color:white;" onclick="hideallmsgs();">Back</a>
            
            <br/>
            <br/>
            <br/>
            <br/>
            <div  data-theme="b" align="center">
             <img src="{!URLFOR($Resource.crushednuts)}" alt="Smiley face" class="checkbox-topping-one-image" style="display:none;"/>
               <img src="{!URLFOR($Resource.oreos)}" alt="Smiley face" class="checkbox-topping-two-image" style="display:none;"/>
                <img src="{!URLFOR($Resource.flakes)}" alt="Smiley face" class="checkbox-topping-three-image" style="display:none;"/>
            </div>
        </div> 
        
    </body> 
    </form>    
</apex:page>
