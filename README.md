# GoodsNStuff

Goods 'n Stuff is a fake online retailer where you can buy your favorite goods and stuff.  More specifically, 
the retailer currently sells three items:
* Ron’s Custom Canoe whose price rotates between $250 and $500
* Ron’s Gingerbread House whose price rotates between $5 and $15
* April’s Marshmallow Ron whose price rotates between $15 and $25

You can access the online retailer at [https://goodsnstuff-xyngs.mongodbstitch.com](https://goodsnstuff-xyngs.mongodbstitch.com).

Here is how the prices are rotated behind the scenes every 10 minutes:
1. A GitHub Action stored in [updatePricesAndPushChanges.yml](/.github/workflows/updatePricesAndPushChanges.yml) runs every 10 minutes. 
The Action executes the following steps:
    1. Checks out this code repo
    1. Updates the prices of each of the items using sed
    1. Commits the changes
    1. Pushes the changes to the repo
1. The push to the repo triggers a [MongoDB Stitch](http://bit.ly/Stitch_Lauren) 
deployment so the online files are updated.
