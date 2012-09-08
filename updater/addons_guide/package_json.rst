############################
package.json Documentation
############################




Examples
=================================

Single Addon
------------------------
::

	{
		"schema_version": "1.0",
		"name" : "channel_images",
		"label": "Channel Imaes",
		"version": "5.1",
		"types": ["module","fieldtype","extension"],
		"paths": {
			"system": [
				"system/expressionengine/third_party/channel_images"
			],
			"themes": [
				"themes/third_party/channel_images"
			]
		}
	}


Multiple Addons
------------------------
::

	{
		"schema_version": "1.0",
		"addons": [
			{
				"name" : "br",
				"label": "BR Shorthand",
				"version": "1.0.0",
				"types": ["plugin"],
				"paths": {
					"system": [
						"system/expressionengine/third_party/br"
					]			}
			},
			{
				"name" : "brilliant_retail",
				"label": "BrilliantRetail",
				"version": "1.1.6.0",
				"types": ["module","fieldtype","extension"],
				"paths": {
					"system": [
						"system/expressionengine/third_party/brilliant_retail"
					],
					"themes": [
						"themes/third_party/brilliant_retail"
					],
					"root": [
						"media"
					]
				}
			},{
				"name" : "cron",
				"label": "ExpressionEngine Cron",
				"version": "1.1.1",
				"types": ["plugin"],
				"paths": {
					"system": [
						"system/expressionengine/third_party/cron"
					]
				}
			},{
				"name" : "poe",
				"label": "BrilliantRetail Poe",
				"version": "1.0.4",
				"types": ["fieldtype"],
				"paths": {
					"system": [
						"system/expressionengine/third_party/poe"
					]
				}
			},{
				"name" : "shortee",
				"label": "Shortee",
				"version": "1.0",
				"types": ["plugin"],
				"paths": {
					"system": [
						"system/expressionengine/third_party/shortee"
					]
				}
			},{
				"name" : "snippet",
				"label": "Snippet",
				"version": "2.2",
				"types": ["plugin"],
				"paths": {
					"system": [
						"system/expressionengine/third_party/snippet"
					]
				}
			},{
				"name" : "tweetline",
				"label": "Tweetline",
				"version": "2.3",
				"types": ["plugin"],
				"paths": {
					"system": [
						"system/expressionengine/third_party/tweetline"
					]
				}
			}
		]
	}
