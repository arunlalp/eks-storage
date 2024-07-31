# eks-storage

## `envsubst` and `EOF` template
```
envsubst <<EOF > deployment.yaml

EOF
```

## Create an EBS volume
```
volume_id=$(aws ec2 create-volume \
  --availability-zone us-west-2a \
  --size 20 \
  --volume-type gp2 \
  --tag-specifications 'ResourceType=volume,Tags=[{Key=Name,Value=MyNewVolume}]' \
  --output json | jq -r '.VolumeId')

echo "Created volume with ID: $volume_id"
```