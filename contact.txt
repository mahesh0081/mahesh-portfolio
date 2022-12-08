<?php

$name = $_POST['name'];
$email = $_POST['email'];
$subject = $_POST['subject'];
$message = $_POST['message'];

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\SMTP;
use PHPMailer\PHPMailer\Exception;


require 'PHPMailer/Exception.php';
require 'PHPMailer/SMTP.php';
require 'PHPMailer/PHPMailer.php';

$mail = new PHPMailer(true);
try {
  
    $mail->isSMTP();                                            
    $mail->Host       = 'smtp.gmail.com';
    $mail->SMTPAuth   = true;
    $mail->Username   = 'maheshsonawane2811@gmail.com';
    $mail->Password   = 'ndrgkyrxluhualvq';
    $mail->SMTPSecure = PHPMailer::ENCRYPTION_SMTPS;
    $mail->Port       = 465;
    

    $mail->setFrom('maheshsonawane2811@gmail.com');
    $mail->addAddress('maheshsona28@gmail.com');

    

    $mail->isHTML(true);
    $mail->Subject = 'Contact US';
    $mail->Body    = "Name: $name <br> Email: $email <br> Subject: $subject <br> Message: $message";

  
    $mail->send();
    echo "<script>alert('Message has been sent')</script>";
} catch (Exception $e) {
    echo "<script>alert('Message could not be sent. Mailer Error: {$mail->ErrorInfo}')</script>";
}

>
