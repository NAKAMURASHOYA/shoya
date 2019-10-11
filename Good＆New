　//　指定した時間にGood＆Newを起動する
   function setTrigger(){
  　　var today = new Date();
  　　var setTime = new Date();
  　　setTime.setHours(時)
  　　setTime.setMinutes(分)
     ScriptApp.newTrigger('main').timeBased().at(setTime).create();
   }

   //　土日祝日を判定する
   function isBusinessDay(){
     var today = new Date();
     var weekInt = today.getDay();
     if (weekInt <= 0 || 6 <= weekInt) {
       return true;
     }
     var calJa = CalendarApp.getCalendarByName('日本の祝日');
     if(calJa.getEventsForDay(today).length > 0){
       return false;
     }
     return true;
     }
     
   //ChatWorkを送信する　//シートを取得する（下記、ロジック）
    function main(){
     var ss = SpreadsheetApp.getActiveSpreadsheet();
     var sheet = ss.getSheets()[0];
     var range = sheet.getRange("A1:A22");  
     var sheet = ss.getSheetByName('★');
     var myCell = sheet.getActiveCell(); //アクティブセルを取得
     var number1 = sheet.getRange('B1').getValue();
     var number2 = sheet.getRange('B2').getValue();
     var number3 = sheet.getRange('B3').getValue();
     var number4 = sheet.getRange('B4').getValue();
     
   //ChatWorkに送信する内容 
     var notify_body 
     = "[info][title]本日のGood＆Newのメンバーです。[/title][toall]\n"
     + "【A：場所1】"  + number1 + "\n[hr]"
     + "【B：場所2】"  + number2 + "\n[hr]"
     + "【C：場所3】"  + number3 + "\n[hr]"
     + "【D：場所4】"  + number4 + "\n[/info]";

   //ChatWorkに送信する
     var roomId = "RoomID"//ルームIDを入力
     var client = ChatWorkClient.factory({token: "ChatWorkAccessToken"});//チャットワークのアクセストークンを入力
     client.sendMessage({room_id: roomId, body: notify_body});
     
   //メンバーをランダムにシャッフルさせる（Randomizes the range）
     range.randomize();

   //トリガーを削除する
   function delTrigger(){
     var triggers = ScriptApp.getProjectTriggers();
       for(var i=0; i < triggers.length; i++) {
       if (triggers[i].getHandlerFunction() == "main") {
         ScriptApp.deleteTrigger(triggers[i]);
     }
     }
     }
     }
