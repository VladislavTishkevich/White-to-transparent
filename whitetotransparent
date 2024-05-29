<?php var_dump('Start');
		$urlval = 'Way to your png';
		var_dump(file_exists($urlval)); 
		$picture = imagecreatefrompng($urlval);
		
		$img_w = imagesx($picture);
		$img_h = imagesy($picture);

		$newPicture = imagecreatetruecolor( $img_w, $img_h );
		imagesavealpha( $newPicture, true );
		$rgb = imagecolorallocatealpha( $newPicture, 0, 0, 0, 127 );
		imagefill( $newPicture, 0, 0, $rgb );
		
		//for white (higher mean more transparent)
		$hardenes = 1;
		if($hardenes == 1){
			$finishcolor = 250;
		}elseif($hardenes == 2){
			$finishcolor = 240;
		}elseif($hardenes == 3){
			$finishcolor = 230;
		}elseif($hardenes == 4){
			$finishcolor = 220;
		}
		$retarray = [];
		for($red = 255; $red >= $finishcolor; $red--){
			for($green = 255; $green >= $finishcolor; $green--){
				for($blue = 255; $blue >= $finishcolor; $blue--){
					$newarr =  [
						"red" => $red,
						"green" => $green,
						"blue" => $blue,
						"alpha" => 0
					];
					array_push($retarray, $newarr);
				}
			}
		}
		$resultremoved = 0;
		for( $x = 0; $x < $img_w; $x++ ) {
			for( $y = 0; $y < $img_h; $y++ ) {
				$target = imagecolorat( $picture, $x, $y );
				$RGB = imagecolorsforindex($picture, $target);
				$bAllowed = true;
				$icnt = true;
				$RRGB = $RGB['red'];
				$GRGB = $RGB['green'];
				$BRGB = $RGB['blue'];
				$RGBparam = $RRGB.'+'.$GRGB.'+'.$BRGB;
				foreach($retarray as $removedRGB){
					$Rcol = $removedRGB['red'];
					$Gcol = $removedRGB['green'];
					$Bcol = $removedRGB['blue'];
					if($Rcol == $RRGB && $Gcol == $GRGB && $Bcol == $BRGB){
						$bAllowed = false;
						$resultremoved++;
					}
				}
				if($bAllowed === true){         
					imagesetpixel( $newPicture, $x, $y, $target );
				}           
			}
		}
		$result = 'Way to result png';
		imagepng($newPicture, $result);
		var_dump('Deleted: '.$resultremoved.' pixeles'); 
		var_dump('Finish');
	?>
