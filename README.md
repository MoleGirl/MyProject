            HttpURLConnection urlConnection = (HttpURLConnection) url.openConnection();  
            urlConnection.setConnectTimeout(3000);  
            urlConnection.setRequestMethod("POST");  
            urlConnection.setDoInput(true);// 从服务器获取数据  
            urlConnection.setDoOutput(true);// 向服务器写数据  
            // 获得上传信息的字节大小以及长度  
            byte[] mydata = buffer.toString().getBytes();  
            // 表示设置请求体的类型是文本类型  
            urlConnection.setRequestProperty("Content-type", "application/x-www-from-urlencoded");  
            urlConnection.setRequestProperty("Content-length", String.valueOf(mydata.length));  
            // 获得输出流,向服务器输出数据  
            OutputStream outputStream = urlConnection.getOutputStream();  
            outputStream.write(mydata, 0, mydata.length);  
            outputStream.close();  
            int responseCode = urlConnection.getResponseCode();  
            if (responseCode == 200) {  
                return changeInputStream(urlConnection.getInputStream(), encode);  
            }  
