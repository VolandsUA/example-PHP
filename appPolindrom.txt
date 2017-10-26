<?php
function isPolindrom($x)
{
    $s = (string)$x;
    $r = strrev($s);
    if ($s === $r) {
        return true;
    }
    return false;
}

function isPrime($number, $array)
{
    foreach ($array as $value) {
        if ($value > ceil($number / 2)) {
            return true;
        }
        if (!($number % $value)) {
            return false;
        }
    }
    return true;
}

function arrPrimeNums()
{
    $i = 2;
    $arr = [];
    while (true) {
        if (isPrime($i, $arr)) {
            array_push($arr, $i);
        }
        if ($i >= 99999) {
            break;
        }
        ++$i;
    }
    $arrRez = array_filter(array_reverse($arr), function ($v) {
        return $v > 9999;
    });
    return $arrRez;
}

function selectMaxPolindrom($arr)
{
    $arrPolindromMax = [];
    foreach ($arr as $val) {
        foreach ($arr as $value) {
            $result = $val * $value;
            if ((isPolindrom($result)) && ($result > $arrPolindromMax['polindrom'])) {
                $arrPolindromMax = [
                    'polindrom' => $result,
                    'num1' => $val,
                    'num2' => $value
                ];
            }
        }
    }
    return $arrPolindromMax;
}

$result = selectMaxPolindrom(arrPrimeNums());
echo 'MaxPolindrom = ' . $result['polindrom'] . "\n";
echo 'multiplier_1 = ' . $result['num1'] . "\n";
echo 'multiplier_2 = ' . $result['num2'] . "\n";
