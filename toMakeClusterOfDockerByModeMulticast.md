## first modify two files 
* aerospike.conf
    
    uncommment access-address line, define its value as variable ACCESSADDRESS  and network mode as multicast
    
* entrypoint.sh

    add ** sed -i "/s/ACCESSADDRESS/${ACCESSADDRESS}/g" /etc/aerospike/aerospike.conf **  in the first line.
    
## rebuild a new images copying the above two files into this new images based on the Dockerfile given.

    docker build -t newImageName .
    
## run this new image in host mode by passing ACCESSADDRESS as env variable.

    docker run -tid --name moon --net=host -e "ACCESSADDRESS=X.X.X.X" -p 3000:3000 -p 3001:3001 -p 3003:3003 newImageName
    
    so the access-address can have an address other node in the cluster can access to it.
    
    
    
 ## so is the way in mode mesh
