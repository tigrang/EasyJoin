EasyJoin
========

CakePHP plugin - Easily create joins for your associated models.

EasyJoin makes using ad-hoc joins simple and quick. No longer do you have to deal with unbinding/bindings model on-the-fly or writing `join` arrays to force Cake to use joins instead of doing multiple queries. EasyJoin will automatically detect the relationship between model and create joins array for you. 

# Requirments
* PHP >= 5.3.0
* CakePHP >= 2.0

# Installation

_[Manual]_

1. Download this: [http://github.com/tigrang/EasyJoin/zipball/master](http://github.com/tigrang/EasyJoin/zipball/master).
2. Unzip
3. Copy the resulting folder to `app/Plugin`
4. Rename the folder to `EasyJoin`

_[GIT Submodule]_

In your app directory run:

	git submodule add https://github.com/tigrang/EasyJoin.git Plugin/EasyJoin
	git submodule init
	git submodule update

_[GIT Clone]_

In your plugin directory run:

	git clone https://github.com/tigrang/EasyJoin.git

## Usage

### AppModel

	App::uses('EasyJoinAppModel', 'EasyJoin.Model');
	class AppModel extends EasyJoinAppModel {
	}

### Example

	public function findBySubscriber($id) {
		App::uses('Course', 'Model');
		return $this->find('all', array(
			'conditions' => array('Subscription.subscriber_id' => $id),
			'joins' => array(
				self::joinLeft('Subscription'),
				self::joinLeft('Course'),
				self::joinLeft('Professor'),
				Course::joinLeft('Department'),
				Course::joinLeft('Client'),
			),
		));
	}

# Credits

EasyJoin was inspired by the article "[Restoring elegance to CakePHP — doing multiple joins The Right Way™](http://cfc.kizzx2.com/index.php/restoring-elegance-to-cakephp-doing-multiple-joins-the-right-way/)"