- You may need to ((626353e0-b9f0-44c4-aba4-c9185da642e7))
- Install tethysatcore version 0.11.0 by running `tethys install -d`
- ```python
  	from tethysext.atcore.models.app_users import SpatialResource, initialize_app_users_db
  
  Class GsshaModel(SpatialResource):
    TYPE= 'gssha_model'
    DISPLAY_TYPE_SINGULAR = 'GSSHA Model'
    DISPLAY_TYPE_PLURAL = 'GSSHA Models'
    
    __mapper_args = {
      'polymorphic_identify': TYPE
    }
    
  def init_primary_db(engine,first_time):
    initialize_app_users_db(engine,first_time)
  ```
- app.py
- ```python
  from tethys_sdk.app_settings import PersistentStorageDatabaseSettings
  
  
  def persistent_store_settings(self):
    ps_settings = {
      PersistentStorageDatabaseSettings(
        name = 'primary_db',
        description = 'Primary database for this app',
        initializer = "gssha_explorer.models.init_stores",
        required = True,
        spatial = True
      ),
    }
  ```
- Tethys syncstores not working
- Unistall app and install again.
- assign a db persistent storage in tethys portal
- run syncstores
- add in the url_maps the following
	- ```python
	  from tethysext.atcore.urls import app_users
	  
	  app_users_urls = app_users.urls(
	    url_map = UrlMap,
	    app=self,
	    persistent_store_name = 'primary db',
	    base_template = 'gssha_explorer/base.html'
	  )
	  url_maps.extend(app_users_urls)
	  ```
- add the following to base.html
- ```html
  {% url 'gssha_explorer:home' as home_url %}
  {% url 'gssha_explorer:app_users_manage_users' as manage_users_url %}
  {% url 'gssha_explorer:app_users_manage_organizations' as manage_organizations_url %}
  {% url 'gssha_explorer:app_users_user_account' as user_account_url %}
  <li {% if request.path == home_url %}class="active"{% endif %}><a href= {{ home_url }}>Home</a></li>
  <li {% if request.path == manage_users_url %}class="active"{% endif %}><a href= {{ manage_users_url }}>Users</a></li>
   
  
  
  {% block content_dependent_styles %}
  	{{ block_super }}
  	<link href="{% static 'atcore/css/flat_nav.css' %}" rel="stylesheet"/>
  {{ endblock }}
  ```
- Go to app.py and implement permissions
	- ```python
	  def permissions(self):
	    from tethysext.atcore.services.app_users.permissions_manager import AppPermisionManager
	    from tethysext.atcore.permissions.app_users import PermissionsGenerator
	    
	    
	    pm = AppPermissionsManager(self.namespace)
	    pg = PermissionsGenerator(pm)
	    permissions = pg.generate()
	    
	    return permissions
	  ```