# Project--slot--rpl
slot_machine_project.html
        <div class="modal-header">
          <h5 class="modal-title">Pay Table</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">

        </div>
      </div>
    </div>
  </div>
  <script src="https://unpkg.com/@n1md7/html-table-builder@1.0.1/dist/table_builder.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
  <script async defer src="https://buttons.github.io/buttons.js"></script>
</body>
</html>
.github/workflowshttps://github.com/kojaynahtul-hub/Project--slot--rpl/actions/workflows/static.yml/badge.svg?branch=main&event=deployment_status
    <!-- Winner Display -->
    <div class="winner-display mb-3">
      <span>WIN: <span id="win-amount">$</span></span>
    </div>

    <!-- Canvas Placeholder -->
    <canvas id="slot" width="440" height="240"></canvas>

    <!-- Button Controls -->
    <div class="controls d-flex align-items-end px-1 mt-3">
      <div class="text-warning left d-flex flex-column align-items-start justify-content-between h-100">
        <span>Credit: <span id="credits" class="credit text-white">$400</span></span>
        <span>Bet: <span id="bet" class="bet text-white">$10</span></span>
      </div>
      <div class="mx-4 middle d-flex align-items-end justify-content-between">
        <button id="minus-bet" class="bet-action-btn">
          <i class="fas fa-minus"></i>
        </button>
        <button class="align-items-center d-flex gap-2" id="spin-manual">
          <i class="fas fa-sync-alt"></i>
          <b>SPIN</b>
        </button>
        <button id="plus-bet" class="bet-action-btn">
          <i class="fas fa-plus"></i>
        </button>
      </div>
      <div class="right d-flex flex-column align-items-end justify-content-between gap-1">
        <button class="align-items-center d-flex gap-1" id="pay-table" data-bs-toggle="modal" data-bs-target="#pay-table-modal">
          <i class="fas fa-table"></i>
          <b>Pay Table</b>
        </button>
        <button class="align-items-center control-btn d-flex gap-1" id="spin-auto">
          <i class="fas fa-play"></i>
          <b>AUTO | OFF</b>
        </button>
      </div>
    </div>
  </div>[![.github/workflows/static.yml](https://github.com/kojaynahtul-hub/Project--slot--rpl/actions/workflows/static.yml/badge.svg?event=check_run)](https://github.com/kojaynahtul-hub/Project--slot--rpl/actions/workflows/static.yml)

	
