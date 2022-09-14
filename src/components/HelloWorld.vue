<template>
  <div>  
    
    <div class="hello mobile-table wrapper">
      <table border="1" rules="all" cellspacing="10" cellpadding="0" class="iksweb">
        <tr>
          <th>№</th>
          <th>ШИР.</th>
          <th>ВЫС.</th>
          <th>Площ.</th>
          <th>ШТ.</th>
          <th>УПР.</th>
          <th>НАИМЕНОВАНИЕ</th>
          <th>СТОИМОСТЬ</th>
          <th>СУММА</th>
        </tr>
        <tr v-for="item, i in array" :key="item.id">
          <td>{{++i}}</td>
          <td>{{item.width}}</td>
          <td>{{item.height}}</td>
          <td>{{item.Square}}</td>
          <td>{{item.count}}</td>
          <td style="max-width: 20px;"><input type="text" class="input-td">{{}}</td>
          <td><input type="text" class="input-td">{{}}</td>
          <td>{{item.price}}</td>
          <td>{{item.An.toFixed(0)}}</td>
        </tr>
      </table> 
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    array: {
      type: Array
    },
  },
}
</script>

<style scoped>
	table.iksweb{text-decoration: none;border-collapse:collapse;text-align:left;color:#000000;}
	table.iksweb th{font-weight:normal;font-size:13px; color:#ffffff;background-color:#181824;}
	table.iksweb td{font-size:13px;color:#000000;}
	table.iksweb td,table.iksweb th{white-space:pre-wrap;padding:10px 10px;line-height:13px;vertical-align: middle;border: 1px solid #354251;}	table.iksweb tr:hover{background-color:#f9fafb}
	table.iksweb tr:hover td{color:#354251;cursor:pointer;}
	.mobile-table{width: 100%; max-width: 100%; overflow-x: auto;}

  .input-td {
    margin: 0;
    padding: 0;
    border: 0;
    width: 130px;
  }
</style>
