<?php
// The target M3U8 URL
$targetUrl = 'https://live.881903.com/edge-aac/881hd/playlist.m3u8';

// Initialize a cURL session
$ch = curl_init($targetUrl);

// Custom headers to simulate a browser
$headers = [
    'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)',
    'Referer: https://www.881903.com/',
    'Origin: https://www.881903.com'
];

// Set cURL options
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
curl_setopt($ch, CURLOPT_HEADER, false);

// Optional: Forward query parameters from client
if (!empty($_GET)) {
    $targetUrl .= '?' . http_build_query($_GET);
    curl_setopt($ch, CURLOPT_URL, $targetUrl);
}

// Execute and capture the output
$response = curl_exec($ch);

// Check for cURL errors
if (curl_errno($ch)) {
    http_response_code(500);
    echo "cURL error: " . curl_error($ch);
    exit;
}

$contentType = curl_getinfo($ch, CURLINFO_CONTENT_TYPE);
curl_close($ch);

// Set proper headers for M3U8
header("Content-Type: $contentType");
header('Access-Control-Allow-Origin: *');

// Output the content
echo $response;
?>
