方法一
---
将table标签，包括tr、td等对json数据进行拼接，将table输出到表格上实现，这种方法的弊端在于输出的是伪excel，虽说生成xls为后缀的文件，但文件形式上还是html，代码如下

    <html>
    <head>
        <p style="font-size: 20px;color: red;">使用table标签方式将json导出xls文件</p>
        <button onclick='tableToExcel()'>导出</button>
    </head>
    <body>
    <script>

    function tableToExcel(){
        //要导出的json数据
        var jsonData = [
        {
            name:'路人甲',
            phone:'123456',
            email:'123@123456.com'
        },
        {
            name:'炮灰乙',
            phone:'123456',
            email:'123@123456.com'
        },
        {
            name:'土匪丙',
            phone:'123456',
            email:'123@123456.com'
        },
        {
            name:'流氓丁',
            phone:'123456',
            email:'123@123456.com'
        },
        ]
        //列标题
        var str = '<tr><td>姓名</td><td>电话</td><td>邮箱</td></tr>';
        //循环遍历，每行加入tr标签，每个单元格加td标签
        for(let i = 0 ; i < jsonData.length ; i++ ){
            str+='<tr>';
            for(let item in jsonData[i]){
            //增加\t为了不让表格显示科学计数法或者其他格式
                str+=`<td>${ jsonData[i][item] + '\t'}</td>`; 
            }
            str+='</tr>';
        }
        //Worksheet名
        var worksheet = 'Sheet1'
        var uri = 'data:application/vnd.ms-excel;base64,';

        //下载的表格模板数据
        var template = `<html xmlns:o="urn:schemas-microsoft-com:office:office" 
        xmlns:x="urn:schemas-microsoft-com:office:excel" 
        xmlns="http://www.w3.org/TR/REC-html40">
        <head><!--[if gte mso 9]><xml><x:ExcelWorkbook><x:ExcelWorksheets><x:ExcelWorksheet>
        <x:Name>${worksheet}</x:Name>
        <x:WorksheetOptions><x:DisplayGridlines/></x:WorksheetOptions></x:ExcelWorksheet>
        </x:ExcelWorksheets></x:ExcelWorkbook></xml><![endif]-->
        </head><body><table>${str}</table></body></html>`;
        //下载模板
        window.location.href = uri + base64(template)
    }
        //输出base64编码
    function base64 (s) {
        return window.btoa(unescape(encodeURIComponent(s)))
    }
    </script>
    </body>
    </html>

方法二
---
通过将json遍历进行字符串拼接，将字符串输出到csv文件，代码如下

    <html>
    <head>
        <p style="font-size: 20px;color: red;">使用a标签方式将json导出csv文件</p>
        <button onclick='tableToExcel()'>导出</button>
    </head>
    <body>
    <script>

    function tableToExcel(){
        //要导出的json数据
        var jsonData = [
        {
            name:'路人甲',
            phone:'123456789',
            email:'000@123456.com'
        },
        {
            name:'炮灰乙',
            phone:'123456789',
            email:'000@123456.com'
        },
        {
            name:'土匪丙',
            phone:'123456789',
            email:'000@123456.com'
        },
        {
            name:'流氓丁',
            phone:'123456789',
            email:'000@123456.com'
        },
        ]
        //列标题，逗号隔开，每一个逗号就是隔开一个单元格
        let str = `姓名,电话,邮箱\n`;
        //增加\t为了不让表格显示科学计数法或者其他格式
        for(let i = 0 ; i < jsonData.length ; i++ ){
            for(let item in jsonData[i]){
                str+=`${jsonData[i][item] + '\t'},`; 
            }
            str+='\n';
        }
        //encodeURIComponent解决中文乱码
        let uri = 'data:text/csv;charset=utf-8,\ufeff' + encodeURIComponent(str);
        //通过创建a标签实现
        var link = document.createElement("a");
        link.href = uri;
        //对下载的文件命名
        link.download = "json数据表.csv";
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
    }

    </script>
    </body>
    </html>
    [TOC]