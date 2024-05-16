docker pull infracloudio/csvserver:latest
docker pull prom/prometheus:v2.45.2

git clone https://github.com/infracloudio/csvserver.git  mkdir solution
cd solution

docker run -d infracloudio/csvserver:latest  docker logs e535f59557d 
vim gencsv.sh

Added content in file by pressing I key to insert  #!/bin/bash

if [ "$#" -ne 2 ]; then
    echo "Usage: $0 <start_index> <end_index>"
    exit 1
fi

start_index=$1
end_index=$2

if [ $start_index -ge $end_index ]; then
    echo "Error: Start index must be less than end index."
    exit 1
fi

filename=“input”data

echo "Generating $filename..."

for ((i=start_index; i<=end_index; i++)); do
    rand_num=$((1 + $RANDOM ))
    echo "$i,$rand_num" >> "$filename"
done

echo "File $filename generated successfully."  now saved it by pressing Esc key with :wq  gaved permission : chmod +x gencsv.sh  run the bash file:  ./gencsv.sh 2 8  verified output : cat inputdata  docker run -d -v "$(pwd)/inputdata:/csvserver/inputdata”  infracloudio/csvserver:latest
 to check status ran docker ps -a

5 point copied commit id i.e. 6ff7425ab58f docker exec -it 6ff7425ab58f /bin/bash  checked port : netstat -tuln got this in output: Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp6       0      0 :::9300                 :::*                    LISTEN  
 it means listening to 9300  stopped container  docker stop 6ff7425ab58f  removed container docker rm 6ff7425ab58f

6 point docker run -d -p 9393:9300 -e CSVSERVER_BORDER=Orange -v "$(pwd)/inputdata:/csvserver/inputdata" infracloudio/csvserver:latest  checked status by docker ps   now verified desired output on http://localhost:9393  vim part-1-cmd pressed I key to insert data given below  : docker run -d -p 9393:9300 -e CSVSERVER_BORDER=Orange -v "$(pwd)/inputdata:/csvserver/inputdata" infracloudio/csvserver:latest saved it by esc with :wq   curl -o ./part-1-output http://localhost:9393/raw  docker logs  1a09794465ab >& part-1-logs 
  
