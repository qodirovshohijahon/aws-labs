
## Create an Application Load Balancer

- 1. Navigate to **EC2** > **Load Balancers**.

- 2. Click **Create Load Balancer**.

- 3. Click the **Create** button under the **Application Load Balancer** and set the following values:

  - Name: HOLALB
  - Scheme: internet-facing
  - IP address type: ipv4
  - Load Balancer Protocol: HTTP
  - Port: 80
  - Select the VPC.
  - Add the us-east-1a and us-east-1b AZs to your ALB.

- 4. Click Next: Configure Security Settings

Note: Skip this screen, as we are not using HTTPS.

Click Next: Configure Security Groups.

Select to Create a new security group for your ALB, and set the following values:

Name: ALBSG
Description: ALBSG
The default value allows standard HTTP traffic from 0.0.0.0/0 and ::/0 (IPV6), so leave as it.
Click Next: Configure Routing and enter the following values:

Name: ALBTG
Target type: Instance
Protocol: HTTP
Port: 80
Expand Advanced health check settings, and reduce the healthy and unhealthy threshold checks down to 2.

This means the load balancer can respond faster and instances come into service and vice versa.
Click Next: Register Targets.

Click Next: Review.

Make a note of the DNS name associated with the load balancer and open in a new browser tab. You should see a 503 error since we don't have any operational EC2 instances associated with the load balancer.