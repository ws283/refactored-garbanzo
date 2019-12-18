<?php

/* neither
     inventory consideration / the more proper negative items approach , 
   nor 
     mechanism for user-specified rules
   are implemented
*/

class Checkout {
  
  private $total=0;
  
  public $arr_prices= array(
     "ipd"=> array( "listed_price"=>0549.99 , "actual_price"=>0549.99 , "qty_scanned"=>0 , "qty_billed"=>0 )
    ,"mbp"=> array( "listed_price"=>1399.99 , "actual_price"=>1399.99 , "qty_scanned"=>0 , "qty_billed"=>0 )
    ,"atv"=> array( "listed_price"=>0109.50 , "actual_price"=>0109.50 , "qty_scanned"=>0 , "qty_billed"=>0 )
    ,"vga"=> array( "listed_price"=>0030.00 , "actual_price"=>0030.00 , "qty_scanned"=>0 , "qty_billed"=>0 )
    ) ;
    
    /* function __construct(){
    } */
    
    function list(){
      var_dump($this->arr_prices);
    }
    
    function scan($sku){
      if ( array_key_exists($sku, $this->arr_prices)===FALSE){ echo "bad SKU";} else {
        $this->arr_prices[$sku]["qty_scanned"]++ ;
      }
    }
    
    function total(){
      foreach ( $this->arr_prices as $key => $value){ $this->arr_prices[$key]['qty_billed'] = $this->arr_prices[$key]['qty_scanned'] ; }
      
      $this->arr_prices['vga']['qty_billed'] = $this->arr_prices['vga']['qty_scanned'] - ( ( $this->arr_prices['vga']['qty_scanned'] >= $this->arr_prices['mbp']['qty_scanned']) ? $this->arr_prices['mbp']['qty_scanned'] : $this->arr_prices['vga']['qty_scanned'] );
      
      $this->arr_prices['atv']['qty_billed'] -= floor( ($this->arr_prices['atv']['qty_billed'] /3 ) ) ;
      
      if ($this->arr_prices['ipd']['qty_scanned']>4){ $this->arr_prices['ipd']['actual_price']=499.99 ; }
      
      foreach ( $this->arr_prices as $key => $value){
        $this->total += $this->arr_prices[ $key ]['qty_billed'] * $this->arr_prices[$key]['actual_price'] ;
      }
      echo ( "\ntotal : $this->total\n" );
    }
    
}

$co0=new Checkout();
$co0->scan('atv');
$co0->scan('atv');
$co0->scan('atv');
$co0->scan('vga');
$co0->total();

$co1=new Checkout();
$co1->scan('atv');
$co1->scan('ipd');
$co1->scan('ipd');
$co1->scan('atv');
$co1->scan('ipd');
$co1->scan('ipd');
$co1->scan('ipd');
$co1->total();

$co2=new Checkout();
$co2->scan('mbp');
$co2->scan('vga');
$co2->scan('ipd');
$co2->total();



?>
